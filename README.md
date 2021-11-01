# Project 2: Real Estate Valuation Models

---

![](https://imgur.com/PWdTc2e)

## Overview

In this project, I construct three regression models to predict home prices in Ames, Iowa, using real estate data obtained from the Journal of Statistics Education ([website](jse.amstat.org/index-archived.htm)).

## Problem Statement

OppenHouser is a hypothetical real estate company based in Ames, Iowa. The company's business revolves around making cash offers on homes, making repairs on homes and relisting them for sale.

As a data scientist for the company, I have been asked by management to make improvements on its valuation model.

Metrics for success for this project are comparisons of valuation metrics between the current and proposed models. All models will be blind-tested on homes sold in 2010, all other homes to be used for training.

## Data

Data for this project contains 2051 observations with 81 features. For a list of the original features in the data, please visit this ([link](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)).

The following list of features are derived from the original data.

|Feature|Datatype|Description|
|---|---|---|
|**Total Full Bath**|*integer*|**Full Bath** + **Bsmt Full Bath**, total number of full baths|
|**Total SF**|*integer*|**Gr Liv Area** + **Total Bsmt SF**, total square footage of a home|
|**Overall QualCond**|*object*|**Overall Qual** * **Overall Cond**, interaction item|

[`train.csv`](./data/train.csv): Ames, Iowa Real Estate Sales Data

## Modeling

The 'current' model in this scenario is ann Ordinary Least Squares regression.

Subsequent Ridge and LASSO regressions are constructed and compared against the OLS regression. The Ridge and LASSO regressions are each fitted to two lists of predictor variables. The four iterations are then scored and the performance is stored for evaluation.

**Be advised**: complexity of the Ridge and LASSO regression models may cause long runtimes.

## Analysis

All prospective models scored higher than the OLS model. The LASSO model with new predictors was the least overfit, had the highest $R^2_{test}$ and lowest root mean squared error.

## Recommendation

I recommend that management adopt LASSO (with new predictors) to capitalize on the biggest decrease in RMSE.

Considering the company's business model is to buy homes, repair them, and re-list the homes, I would advise that the company offer lower than the asking price for homes and use the repairs required as justification.

Last note:

The model is overestimating prices. The model is trained on two years of data prior to the financial crisis of 2008. The significantly lower residuals for 2010 may be indicative of the latent effect of the crisis. Additionally, I recommend re-examining the model more frequently to curtail the model's RMSE as the housing market worsens.