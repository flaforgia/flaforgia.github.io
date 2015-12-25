---
title       : Application For CO2 Prediction
subtitle    : Cars Sold In France In 2015
author      : Francois Laforgia
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Presentation Of The Original Study 
# Why cars?
* Cars are not the only one to emit CO2 but they are the one on which the individuals can have an influence.
* Transportation causes 31% of the CO2 emission in the US and the cars emit one-fith of the total CO2 emissions in Europe.

# Why CO2?
* CO2 is one of the main cause of the greenhouse effect which causes of the Global Warming.
* CO2 is strongly linked to the gas mileage which make it easy to predict (univariate linear model).

# Results
* The original study is detailed in a final report available on github (https://github.com/flaforgia/DataProduct).
* The predictive model is used in a shiny application (https://flaforgia.shinyapps.io/ShinyCode).

---  

## The Application (1)
# Overview
* Allow user to predict the level of CO2 emission for a specific gas mileage.
* Use the European Mileage unit, which is liter per 100 kms.
* Based on a prediction model describe in the study "CO2 emission of the cars sold in France in 2015".
* Limited to diesel and gasoline because they are the main types of fuel used in France (~ 94% of the total sales).

# Format
* Web application.
* Written in R with the shiny package.
* Hosted on the shiny apps web site.
* Publicly available.

--- 

## The Application (2)
# Model
* Univariate Linear Model

```r
paste("CO2 emission for gasoline:",round(predict(modelFit.co2.ES,newset2),2),"g/km.")
```

```
## [1] "CO2 emission for gasoline: 83.14 g/km."
## [2] "CO2 emission for gasoline: 86.37 g/km."
```
# Shiny server
* Active code:
    + Read the csv dataset and perfom data manipulation
    + Generate the models  
* This code is executed outside the shinyServer and thus it is independant of the user session. Speed-up the shinyServer code (no need to read the csv each time)
* Use a reactive expression to predict the value depending on the input parameter.

---
## The Application (3)
# User Interface
* Allows the user to:
    + Choose the gas type
    + Enter the gas mileage in liter per 100 kms
    + Usage of the UI is provided in the sidebar panel

# Next Steps
* Increase the localisation to the rest of the world.
* Add more pollutants (NOx for example)
* Add more gas type (LPG for example)
