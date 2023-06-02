# Assessing the Impact of Large Language Models

![Created using Midjourney](/assets/human_robot_look_at_each_other.png)

## Introduction
Since the launch of ChatGPT large language models (LLMs) have taken the world by storm and each enterprise is reevaluating 
its AI strategy and wondering what LLMs generally and commercial models like ChatGPT and Bard especially 
will mean for their business. In this piece we're trying to look beyond the current hype surrounding the latest models
and look into the midterm and longterm future of NLP techniques and related areas to give some orientation or more humbly 
hints into some directions to ponder which hopefully will survive the headlines of today.
To this end we broaden the perspective with highlighting the historical trajectory from which all this started and even get
into somewhat philosophical territory in the hope to get a glimpse of where all this stuff is headed, what has been achieved, what is missing,
what is to be expected.

## History

![Created using Mathematica](/assets/timeline_of_large_language_models.png)

- **Late 1980s to mid 1990s**: The foundations of neural networks and basic language models are developed.

- **2001**: Yoshua Bengio, Réjean Ducharme, Pascal Vincent, and Christian Janvin published a paper on a neural probabilistic language model, a significant early work in using neural networks for language processing.

- **2003**: Bengio and his team continued to improve upon their initial models, which helped spark broader interest in the field.

- **2013**: Word2Vec, developed by Tomas Mikolov and his team at Google, made a significant impact by effectively converting words into vectors, which could then be processed by neural networks in a meaningful way.

- **2014**: Sequence to Sequence Learning was introduced by Ilya Sutskever, Oriol Vinyals, and Quoc Le. This was a major advancement, as it led to the development of models that could generate more coherent and meaningful sequences of text.

- **2015**: Attention Mechanism was introduced, making it possible for models to learn to focus on different parts of the input sequence when generating output. This improved the ability of models to handle long sequences of text.

- **2018**: Transformer architecture was introduced in the paper "Attention is All You Need" by Vaswani et al. It was a key development because it enabled much more effective training of large language models.

- **2018**: BERT (Bidirectional Encoder Representations from Transformers) was developed by Google. BERT was significant because it was trained to predict missing words in a sentence, rather than just predicting the next word in a sequence.

- **2019**: GPT-2, developed by OpenAI, made a significant leap in the size of models and their ability to generate surprisingly human-like text. GPT-2 was also notable because of the decision by OpenAI to initially not release the full model due to concerns about potential misuse.

- **2020**: GPT-3 was released by OpenAI. With 175 billion parameters, GPT-3 was an order of magnitude larger than any previous model, and its capabilities reflected that size increase.

- **2021**: Large language models started to see wide deployment in commercial applications, such as customer service, content generation, tutoring, and more.

- **early 2022**: GPT-3.5 was released by OpenAI. These models were described as more capable than previous versions and were trained on data up to June 2021.

- **late 2022**: ChatGPT was released by OpenAI, a model fine-tuned to target conversational usage by a process called reinforcement learning from human feedback (RLHF).

- **early 2023**: a plethora of both commercial models and open source versions of LLMs come forth to counter the dominance of ChatGPT

## Structure of LLMs and Econnomic and Scientific Environment
Large language models (LLMs) like GPT-4 and its successors are based on a type of artificial neural network known as a Transformer, which was introduced in a paper by Vaswani et al. in 2017 titled "Attention is All You Need". These models are designed to understand the context of a piece of text and generate text that aligns with that context.

The structure of a Transformer model is largely divided into an encoder and a decoder, although in models like GPT-3, only the decoder is used. Each part consists of multiple layers of self-attention and feed-forward neural networks. 

One of the crucial components of Transformer-based models is the attention mechanism, which allows the model to focus on different parts of the input sequence when generating output. In particular, these models use a type of attention mechanism known as "scaled dot-product attention." 

The size of LLMs is often characterized by the number of parameters they have. For example, GPT-3 has 175 billion parameters. These parameters are the aspects of the model that are learned from the training data.

In terms of training techniques, these models are trained on a large corpus of text data. During training, the models learn to predict the next word in a sequence of words. This is done using a method known as maximum likelihood estimation (MLE), where the goal is to maximize the probability of the next word given the previous words in the sequence.

The training process requires substantial computational resources and is typically carried out on graphics processing units (GPUs) or tensor processing units (TPUs) due to their ability to perform parallel computations, which is essential for handling the large matrices used in these models.

The training data is passed through the model in batches, and the model's predictions are compared with the actual next words in the sequence. The difference between the predictions and the actual words, known as the loss, is calculated using a function like cross-entropy loss.

To update the model's parameters and minimize the loss, an optimization algorithm such as Adam or Stochastic Gradient Descent (SGD) is used. This is done through a process known as backpropagation.

After training, these models can generate new text by taking in a prompt and producing a sequence of words, predicting each next word based on the previous ones.

Recent advancements in LLM training have involved techniques such as unsupervised learning, transfer learning, and fine-tuning, where a model trained on a general task is adapted for a more specific one. These methods have allowed LLMs to achieve high performance across a variety of tasks. 

It's also important to note that training LLMs comes with challenges, including the need for large amounts of data and computational resources, potential bias in the training data, and the risk of the model generating harmful or misleading content.
## The GPT-H Hypothesis

![Created using Midjourney](/assets/kid_arranging_letters_on_the_floor_scrabble.png)
The capabilities of LLMs in turn dialogue talking, reasoning and instruction following have reached an impressive maturity. These capabilities were discovered by scaling up the models and training them on ever larger text corpora and are therefore referred to as emergent phenomena. It is important to emphasize that they are not built into the models by special training techniques, in fact techniques to bring about these skills are not known. The only technique built into the models and trained is next word prediction.

The dismissive argument that LLMs "are just next word predictors" which often serves to counter the enthusiam showed by people awestruck with the generated responses of e.g. ChatGPT somewhat misses the point and fails in our opinion to assess the rather striking and compelling hypothesis which we call the **GPT-H hypothesis**: Insofar as LLMs generate responses which are eerily close or even indistinguishable to human utterances we have two alternatives.

1. We hit upon another model of language intelligence different from the human brain which is capable of generating nearly the same language artifacts as humans.

2. The human ability to produce, use and reason in language shares a common mechanism with LLMs and the technique of next word prediction.

The second alternative or simplified the statement that humans are in some way General Pretrained Transformers may be outrageous to many. But scientific history should caution us on our thinking that humankind has a special place in nature. As astronomy refuted that we are at the center of the universe and evolution replaced us from the crown of creation to the animal kingdom, AI may teach us that cognition, language and thinking is not as special as we'd like to think. This hypothesis is kind of a glorified Chomsky theory of language: Where Chomsky tried to construct language as an innate mechanism of formal language models built into the human brain, LLMs kind of repeat this with a more complicated and sophisticated version on a probabilistic basis.

Pondering the impact of LLMs one should keep in mind what this hypothesis entails for the advancement of LLMs or AI in general: Namely the explosive hypothesis that LLMs may be likely in the future to invade all kinds of activities connected with language use, thinking and creativity. 

## Gaps and Features
- Hallucinations
- Adversarial Prompting
- Missing Reference to Ground Truth
- QA

### Access to UpToDate Knowledge
### Long Term Memory

### Continuous Learning

### Tool Use

## Long Term Development

### Integrated AI

### Generative AI

### Self Referential AI

### Physical Access

## Immediate and Near Term Impacts

### End of SE Domination

### Document Creation

### Code Generation

### Use of LLMs within Programs

## Mid Term Impacts

### Front End to Everything

### Computer Program Generation


## Long Term Impacts

### Self Referential AI And Exponential Acceleration

### Knowledge Creation and Science

### Creative Industry

### Engineering

## Economic Impacts

### Rise of Mega Monopolies

### Industry Domination

## Conclusion