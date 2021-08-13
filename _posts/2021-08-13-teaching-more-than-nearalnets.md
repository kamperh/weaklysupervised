---
layout: post
title: Teach more than neural networks
description: Using as an example a recent paper from Facebook, I argue why we
    should still teach some classic machine learning approaches.
---

In a [recent paper](https://arxiv.org/abs/2105.11084), Facebook accomplished
something amazing: they were able to train an automatic speech recognition
system without any explicit labelled speech data. Their approach relies on two
data sources:

1. Unlabelled speech in the language of interest.
2. Written text in the language (which they convert to phonemic sequences using
   a character-to-phoneme converter).

Their methodology relies on a type of neural networks called a generative
adversarial network (GAN).[^1]  I don't want to go into all the details here,
but their short two-minute video on their [blog
post](https://ai.facebook.com/blog/wav2vec-unsupervised-speech-recognition-without-supervision/)
gives a relatively good overview of the main idea.

[The Facebook paper](https://arxiv.org/abs/2105.11084) does a good job of
explaining the different components of their system. It also honestly explains
what they had to do to get the approach to work.[^2]

What was most interesting to me was that, if you read between the lines, it is
clear that the fancy GAN-based neural network on its own didn't work out of the
box. The researchers had to incorporate a number of classic machine learning
approaches at different points in their system pipeline, and without these
steps, the overall system didn't work.

These classic methods include:

- *K*-means clustering.
- Principal components analysis (PCA).
- Very careful data pre-processing, for instance in how they dealt with silences.
- A hidden Markov model (HMM) gave best self-training results.

And this is without mentioning the careful experimental design that they had to
do, for instance splitting their datasets appropriately (train, validation,
testing) and measuring performance in an honest way---the basics of good
machine learning.

I am currently teaching an [introductory machine learning
class](http://www.kamperh.com/data414/), and it was encouraging to me to see
how these key classic concepts still play such a key rule in real practical
machine learning applications. So this post hopefully also serves as a bit of
an encouragement for the students taking my class. We need more than just
neural networks to tackle challenging and real engineering and scientific
problems.

* * *

[^1]: I should note that this idea was already proposed a few years ago by [(Liu et al., 2018)](https://arxiv.org/abs/1804.00316), but this paper was the first to show how the approach can be scaled and applied to several different languages apart from English.
[^2]: More machine learning papers should do this. I think it helped a lot that the paper was written in a longer journal format, rather than the shorter conference style.
