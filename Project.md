Developing Data Products Course Project
========================================================

Date: February 21 2015

Purpose of the Course project Shiny App
========================================================

The purpose of the Course project shiny App is to use faithful dataset to demostrate the accuracy of linear prediction

How is works

- User choose one of 272 samples via index in faithful dataset as the testing data
- The app will using the remaing 271 samples to training the linear mode
- The app will return both test sample value and the predicted value from the algorithm

Old Faithful Geyser Data
========================================================

- Description

Waiting time between eruptions and the duration of the eruption for the Old Faithful geyser in Yellowstone National Park, Wyoming, USA.



```
  eruptions waiting
1     3.600      79
2     1.800      54
3     3.333      74
4     2.283      62
5     4.533      85
6     2.883      55
```

<small>The above description is copied from R: Old Faithful Geyser Data help</small>


How to use the App
========================================================

- Go to website: https://jessehliu.shinyapps.io/DevelopingDataProduct/
- Click the "Main page" tab
- Choose the index from 1 to 272 at the left side of panel
- Click the button "Click button to start prediction"
- Both the actual eruption time and the predicted eruption time will be displayed on the righ side of main panel
- Click the "Documentation" tab for help

What is the prediction behind?
========================================================
Below are the R code to perform the prediction

```r
doPrediction <- function(idx)
{
    data_train <- faithful[-idx, ];
    data_testing <- faithful[idx, ];
    eruption.lm = lm(eruptions ~ waiting, data=data_train)

    predict_value = predict(eruption.lm, data_testing)
}

index <- 100
actValue <- faithful[index, 1]
preValue <- doPrediction(index)
```

