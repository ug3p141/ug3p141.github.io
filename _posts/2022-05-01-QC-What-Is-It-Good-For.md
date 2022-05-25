## What Is Quantum Computing Good for?

Quantum Computing (QC) is now a darling of the media, where it is treated either a little bit like science fiction become reality or a technology to be approached with a raised eyebrow. Either way most articles don't seem to know why such a technology exists at all and what to expect of it. This is no surprise given the fantastic titles of papers containing words like "Quantum Supremacy" [1]. So expectations range from high to fantastic and some media articles even seem to suggest that QC some time in the future can replace classical computing (CC).

Actually, as new as it feels perhaps to most people the subject has a relatively long history dating back to Feynman's musings about using computers to simulate physics [4] and some even earlier work by russian Mathematician Yuri Manin forty years ago. This was celebrated in a Nature Reviews Physics editorial aptly named "40 years of quantum computing" in 2021 [2].

So what is so special about QC compared to CC and where is its place in computer science? To understand the fundamental difference between QC and CC it's useful to recall their respective basic paradigms of programming and understanding the world in terms of algorithms. First let's recall the algorithmic view of CC. The abstract mathematical description of a computer is based on Universal Turing Machines (TM). This means that a classical computer reads an arbitrary algorithm sequentially encoded in storage (the tape of the TM) and executes it. This is as close to our intuitive understanding of computing as it gets and leads to the usual basic operations one finds in every programming language together with the usual constructs like loops, forks, etc. Thus the TM is an adequate model of computing for most of what we do in the ordinary world including e.g. delivering websites where the "algorithm" is a constant back and forth between user inputs putting some things on the "tape" and server transactions reacting to these inputs. 

Now the computing paradigm for a quantum computer is quite different. There is no such thing as a quantum Turing Machine (well actually there is, s. Wikipedia, but it's a bit of a stretch to try to copy the classical notion). To approach the question it is perhaps easier to describe how a quantum computer works: A quantum computer is set up in an initial (quantum) state, which is evolved according to prespecified quantum gates and at the end the resulting state is measured. It is very important that you don't disturb the thing before the end (in order to keep coherence as physicists say). E.g. if you measure something before the computing is done you totally mess up the computation and can go back to square one. This is in sharp contrast to classical computing where at every corner you can and will inspect the "tape" and the computation happily carries on. So what the quantum computer does is, it effectively simulates or carries out the continuous time evolvement of a quantum state according to the rules of Quantum Mechanics (QM). So the computing model or paradigm of the quantum computer is Schrödinger's equation (SE) [3]. Without knowing much of QM it is easy to understand that SE is the adequate model for QM but not for ordinary problems in our world like bank transactions or serving a website. Thus QC is mainly useful for quantum computing which sounds a bit redundant but is nevertheless true. Why is this tiny field of relevance still important? Because classical computers are principally very inefficient at simulating quantum physics and no improvement to classical computing can remedy this problem. It's no surprise then that the main application areas for quantum computers concern quantum physics or quantum chemistry [5][6]. This is indeed very important considering the rapid miniaturization of electrical and computing components going into territory where classical equations cease to be relevant and very important problems like high temperature superconductivity which are inherently quantum mechanical have to be solved to keep our energy balance in a world threatened by climate change.

Besides these areas there are interesting connections to number theory and a few other problems, which are perhaps a bit more emphasized than they should be (a lot of people will object here I suppose ...). At least the link to number theory namely factorization of prime numbers is so important that it merits mention because of the ability of quantum computers to factorize primes efficiently which is deemed out of reach for classical computers. This would break all of our security infrastructure which is based on the this premise (even if there is no mathematical proof for it). At the time being quantum computers haven't scaled so far to reach this goal and will not for some time in the future.

References

[1] Google paper claiming "Quantum Supremacy": <https://www.nature.com/articles/s41586-019-1666-5>

[2] Nature Editorial: <https://www.nature.com/collections/djhfiebiig/>

[3] Schrödinger's equation: <https://en.wikipedia.org/wiki/Schr%C3%B6dinger_equation>

[4] Feynman, Simulating Physics with Computers: <https://link.springer.com/article/10.1007/BF02650179>, one can find all articles in this volume online

[5] Google Research Publications on QC: <https://research.google/pubs/?area=quantum-computing>

[6] Variational Quantum Algorithms, a review of research on current algorithms for quantum computers: <https://www.nature.com/articles/s42254-021-00348-9>