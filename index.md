---
title       : Growth of Orange Trees App
subtitle    : Course Project - Developing Data Products
author      : Sachin Singh
job         : Software Engineer
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

1. This app was made as a project for Coursera's class on Developing Data Products.
2. It's built using shiny and hosted on shinyapps.io. Click [here][1] to see.
3. This app uses core "Growth of Orange Trees" dataset comes with R.
4. In the dataset, The trunk circumference of 5 trees is measured at 7 different ages, giving a total of 35 datapoints.
5. The format of the dataset is below:
   *  **Tree** - An ordered factor indicating the tree on which the measurement is made. The ordering is according to increasing maximum diameter.
   *  **age** - A numeric vector giving the age of the tree (days since 1968/12/31).
   * **circumference** - A numeric vector of trunk circumferences (mm). This is probably “circumference at breast height”, a standard measurement in forestry.
6. The shiny app applies mixed-effects logistic model to analyze the orange tree growth data.

[1]: https://sachinsingh01.shinyapps.io/prog_ddp_shiny "Shiny App"

--- .class #id

## Using the App

!["app""](ShinyApp.jpg)
Select a particular tree number from radio group and move the slider bar to see the effect. Also, Check multiple tabs (plot, summary, model) for reactive outputs.

--- .class #id

## R Code
e.g. for Tree 1

```r
library(datasets)
fm1 <- nls(circumference ~ SSlogis(age, Asym, xmid, scal), data = Orange, subset = Tree == 1)
fm1
```

```
## Nonlinear regression model
##   model: circumference ~ SSlogis(age, Asym, xmid, scal)
##    data: Orange
##  Asym  xmid  scal 
## 154.2 627.2 362.6 
##  residual sum-of-squares: 177
## 
## Number of iterations to convergence: 0 
## Achieved convergence tolerance: 5.815e-06
```

--- .class #id 

## Graphs
![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) ![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-2.png) 

--- .class #id 

## References
* Draper, N. R. and Smith, H. (1998), Applied Regression Analysis (3rd ed), Wiley (exercise 24.N).
* Pinheiro, J. C. and D. M. Bates (2000). Mixed-effects models in S and S-PLUS. New York: Springer.
* Fournier, D. A., H. J. Skaug, J. Ancheta, J. Ianelli, A. Magnusson, M. N. Maunder, A. Nielsen, and J. Sibert (2012). AD Model Builder: using automatic differentiation for statistical inference of highly parameterized complex nonlinear models. Optimization Methods & Software 27 (2), 233{249.
* Madsen, H. and P. Thyregod (2010). Introduction to General and Generalized Linear Models. Boca Raton, FL: CRC Press.
* Skaug, H. and D. Fournier (2006). Automatic approximation of the marginal likelihood in non-Gaussian hierarchical models. Computational Statistics & Data Analysis 51 (2), 699{709.

Thank You!
