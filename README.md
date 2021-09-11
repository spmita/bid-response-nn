# Interpretable bid-response model using simple neural network



## Background

In pricing analytics, measuring price sensitivity is a common and useful task.  Information on the level of price sensitivity and how this varies by product, customer, channel, time, etc. can be combined with information of how price affects profitability in order to set optimised prices.

Traditionally, econometric models are constructed to predict a volume-related metric such as volume, conversion or market share as a function of explanatory variables including price-like variables such as price, discount and promotions.  In these models the estimated coefficients of the price-like variables can be interpreted as price sensitivities.  In many cases such models are used in price optimisations system.  These typically require that the volume-like metric is expressed as a smooth function of the price-like variables, which is true of the linear and logistic (and other) regression models often used.

A common sales process involves customers requesting quotes for a product or service, receiving a quoted price and either buying or not buying based on that quoted price.  We define the conversion rate to be the proportion of requested quotes in which the customer decides to buy the product or service. Everything else being equal, it is expected that conversion rate decreases as quoted price increases:

![image-20210911223527968](C:\Users\paul_\bid-response-nn\image-20210911223527968.png)

This curve is called the bid-response curve and is traditionally modelled using a logistic regression:
$$
ln(ConversionRate/(1-ConversionRate)) = xB
$$
Where $x$ includes price-like variables and others potentially representing customer, product\service, channel, competition, market and other variables.



## Purpose

The purpose of this is to demonstrate the application of a simple neural network to the problem of measuring useful price sensitivity in a quotation sales process (as described above).  The benefits of this approach are:

1. Modelling of non-linear effects without hand-crafting interactions and transformed features.  .
2. Calculation of price sensitivities, with the same ease-of-interpretation as in a logistic regression model. 
3. Creation of a smooth bid-response curve for each observation in the dataset, appropriate for incorporation into a price optimisation.

Benefit (1) is the natural result of using a neural network.   Benefits (2) and (3) arise from the specific design of the final layer of the network.

