# Diffusion Models: The Main Ideas

![Diffusion Models: The Main Ideas](/assets/diffusion_is_coming.png)

Diffusion Models are the new hot topic in generative AI and used for generating images, text and audio.

This is a post sketching the main ideas of diffusion models. One might ask why I post another take on the topic if the internet is already swarming with explanatory posts and videos. The reason is mostly personal because while there are great resources explaining the actual implementations I had a hard time wrapping my head around the ideas and why it is done the way it is in the first place. So I got back to the original papers searching for answers.

Here I want to share my findings which concern the relevant concepts and ideas of diffusion models neglecting the actual implementations and simplifying it to the basics to be understandable to non-experts - at least I hope so.

I will first sketch some basic technical notions in part one and then in part two I will try to give a more intuitive explanation of the main ideas.
## Foundations
So let's dive right in. The main questions we have to answer first are:

- **Which task are we trying to solve in generative AI?**
- **What is the improvement of diffusion models over previous approaches?**

### Which task are we trying to solve in generative AI?
Citing a forthcoming classic textbook in its second edition: [Probabilistic Machine Learning: Advanced Topics" by Kevin Murphy](<https://github.com/probml/pml2-book>) (s. Chapter 20):

**Definition of generative model**

A generative model is a joint probability distribution $p(x)$, for $x \in X$ where $X$ is the data.

Well that's a bit abstract. Let's try to make it more concrete. Usually we are given the data, say a bunch of pictures of [celebrities](https://paperswithcode.com/dataset/celeba) and our task in generative AI is to create another picture of a celebrity matching the given data.

![Celebrities](/assets/CelebA-0000000002-eeb5e196_D0ltvot.jpg)
*Celebrities from the CelebA dataset*

The central tenet of generative AI is that all we have to do is learn the probability distribution of the data and sample from the learned distribution. So this leads to the next questions: How is the probability distribution actually defined in terms of the data? And what does sampling from a distribution mean exactly?

The first question is in principle pretty easy taking as examples our image dataset: Each image is given as a rectangular grid of pixels with three values at each pixel for the colors. We can arrange these in a sequence e.g. by going from left to right and top to bottom. This gives us a sequence of numbers which we can interpret as a vector. This vector has size number of pixels times three. Say for the celeb dataset 218 x 178 x 3 = 116412. So we have a point cloud in an 116412 dimensional space. A probability distribution on the other hand is a function which assigns a probability to each point in this space. And in principle we can go back and forth between point clouds and probability distributions by thinking of the point cloud as an approximation to the continuous distribution.

Here is the simplest nontrivial example of a probability distribution in two dimensions with a point cloud sampled from it:

![switching between point cloud and probability distribution](/assets/point_cloud_distribution_v1.png)
*Switching between point cloud and probability distribution*

So far so good. But if we have the distribution in terms of the data, we can now simply sample from it to generate a new point which in our example would be a new picture. So what does sampling mean exactly and how can we do it?

As we can infer from the picture above sampling from a distribution means generating data point which are distributed according to the probability density. Thus it doesn't make sense to talk about sampling one point, one has to come up with a procedure which generates hypothetically an infinity of points. Now the main work horse of sampling is the markov chain monte carlo algorithm (MCMC) and its various refinements.

The basic idea with this algorithm to simply start somewhere in space, then move in a random direction, test if it goes uphill in the given probability distribution and if so accept the move. If it goes downhill you accept it only with a certain probability otherwise reject it and stay where you are. That's all, the implementation is really a only a few lines of code. The difficult part is proving mathematically that this algorithm fulfills the definition of sampling i.e. all the points generated are distributed in the end according to the given probability distribution.

### What is the improvement of diffusion models over previous approaches?

This brings us to the question why diffusion models are necessary, what is the improvement over previous approaches? 
The answer to this is found in the foundational paper of diffusion models [1] by Sohl-Dickstein from 2015:

1. MCMC is slow and difficult to parallelize
2. MCMC samples from a so called proposal distribution which is near but not quite the target distribution
3. It is conceptually difficult to marry MCMC with another distribution for conditional inference, think of text to image problems

The main idea of diffusion models is to split up sampling in a two-step process: First we sample from a simple distribution and then move the sampled point into the target distribution. Basically that's it and the intricacies come up with how we actually move the point to the target distribution, which is part two below in my post.

For some reason this paper went unnoticed for several years
![Citation count on paper by Sohl-Dickstein](/assets/sohlpapercitations.png)
*Number of citations of the foundation paper by Sohl-Dickstein et al. over time*

until Sohl-Dickstein and Song published a follow-up paper in 2020 [2] which was picked up by the AI community and led to a flurry of papers and implementations.

## Diffusion Models: The Main Ideas

So let's recap: We are given our target distribution by example as a bunch of points and we want to sample from this distribution. How do we do this?

In their second installment in paper [2] Sohl-Dickstein and Song actually dug up an old paper of Anderson's [3] titled Reverse-time diffusion equation models. What Anderson was concerned with more than 40 years ago was an at that time somewhat obscure question about reversing the flow of stochastic differential equations (SDEs). What is an stochastic differential equation? This is just an ordinary differential equation with some noise added. Usually these are written in the form:
$dx(t) = f(t) dt + g(t) dW$
where $dW$ is the noise actually Brownian motion which simply means that at each time step you draw a random variable from a normal distribution, scale it with the time step and add it to get the direction in which x(t) is heading next.

Here is an illustration of an SDE in two dimensions with pure noise, i.e. $f(t) = 0$ and $g(t) = 1$:

![Random walk in 2D](/assets/stochastic_points.png)
*Random walk in 2D*

The red dots mark the random starting point.

It obviously doesn't make sense to ask about the reversal of time for an individual path because it is random. But you can consider the following question: If I distribute many points as starting points according to a given distribution and evolve all points according to my SDE, then my initial distribution will change over time. If I record all the distributions at each time step, can I find a similar SDE such that the final distribution changes back to the original?


For an SDE with pure noise his result looks like:

$\text{Forward:  } dx(t) = dW $

$\text{Backward: } dx(t) = \nabla \ln{p(x,T-t)} dt + dW $

Where $T$ is the final time for the forward process and the backward process has also to be run from $t=0$ to $t=T$. The complicated part is the gradient of the log of the probability distribution which you have to record during the forward process.

In the forward process, all points are simply shaken up by random noise, independent of each other. So the final distribution after a long enough time will be a normal distribution. And then you can take a bunch of sample points from the normal distribution and run them through the backward process to get back to the original distribution.

An animation of a very simple distribution in two dimensions evolving over time according to the simple pure noise process into a simple gaussian:

![2D double gaussian evolving to simple gaussian](/assets/dist_anim.gif)
*2D double gaussian evolving to simple gaussian*

This result lay dormant for fourty years until Song, Sohl-Dickstein et al. put it to practial use: You have to diffuse your data points e.g. your images with noise and record the resulting intermediate distributions. Then for generating a new image from your target distribution you simply sample a point from a normal distribution in appropriate dimensions which is fast and efficient and run it through the reverse process.

The only complicated part is learning the gradient of the log probability at all intermediate times which is done via a neural network. But this is only done once and then you can sample as many points as you want.

Thus diffusion models need three ingredients:
1. A target distribution given by the set of data points
2. A simple distribution of our choosing to sample from
3. A way to move points from the simple distribution to the target distribution, which is done here via SDEs

## Bits and Pieces

To wrap it up I want to mention that the most difficult part for me is all the jargon surrounding the topic. E.g. the backward process is often called "denoising" which is somewhat misleading in my view, because our desired sample distribution is by choice a sum of independent normal distributions. And of course a bunch of independent random variable always looks like noise.

Connecting with the various implementations there are a few things to mention:
1. Discretized versions of an SDE are Markov processes and this is besides SDEs the other most often cited implementation pioneered by Ho et al. [4].
2. From an abstract point of view we need a mapping between two distributions: The one we sample from and our target. There are various mathematical theories which existed long before diffusion models which explore this topic. One of them is optimal transport theory which is used in the implementation of the Wasserstein Autoencoder. Other theories are termed Schrödinger bridges, stochastic control theory and optimal control theory. All these play into the main idea of trying to make an efficient connection between two distributions. 

I hope this was helpful if you are new to the topic. If you have any questions or comments please let me know.

References:

[1] [Deep Unsupervised Learning using Nonequilibrium Thermodynamics, Sohl-Dickstein et al.](https://arxiv.org/abs/1503.03585)

[2] [Score-Based Generative Modeling through Stochastic Differential Equations, Song, Sohl-Dickstein et al.](https://arxiv.org/abs/2011.13456)

[3] [Reverse-Time Diffusion Equation Models](https://core.ac.uk/download/pdf/82826666.pdf)

[4] [Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239)

[5] [Wasserstein Autoencoder](https://arxiv.org/abs/1711.01558) by Tolstikhin et al.

[6] [Link to Mathematica Code to reproduce the MCMC animation](https://www.wolframcloud.com/obj/ug3.141/Published/MarkovChain.nb)

[7] [Link to Mathematica Code to reproduce the SDE part](https://www.wolframcloud.com/obj/ug3.141/Published/diffusion_models_presentation.nb)
