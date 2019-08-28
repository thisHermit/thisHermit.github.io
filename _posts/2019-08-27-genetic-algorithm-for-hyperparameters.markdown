---
layout: post
title: "Genetic algorithm for hyperparameters"
date: "2019-08-27 17:52:14 +0530"
categories: [genetic-algorithms, ai, machine-learning, neural-network]
---


Upon reading [this](https://towardsdatascience.com/gas-and-nns-6a41f1e8146d) article on Genetic algorithm here, I imagined that it would be amazing to have a genetic algorithm decide the hyperparameters for a neural network like the number of neurons in the different layers and number of layers, etc.

Also another idea that I got was that changing the number of layers or adding or removing a new layer would come at cost. This cost will be modeled by another model. This could be another agent which could baby-sit the entire generation for their evolutionary advances.

But that would prove to be too much for the initial run. As the data required to make proper decisions would come after a large number of generations. So this could be implemented later.

So for now, I would be creating generations and applying genetic algorithm to find the optimal hyperparameters for the various agents.
