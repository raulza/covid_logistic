# Logistic Regression Modeling For Covid
This is a simple way of predicting the total number of deaths or cases by assuming that the growth in these numbers will follow a logistic growth curve.

Virtually every major epidemic has resulted in growth curves that look like this (even in some cases where there is under-testing), and every country has been roughly following this pattern so far.

These results will be updated at midnight pacific time every day by pulling [data from Johns Hopkins](https://github.com/CSSEGISandData/COVID-19), and with more data, the predictions will improve. The model is not likely to work well when the data is still very noisy and a clear trend hasn't emerged, and to give a sense of which predictions are more noisy I have plotted the trends the model is using here:

## Deaths
![Image](deaths.png)
## Confirmed cases
![Image](cases.png)

## How the Model Works

One simple way to fit this model is to plot the number on the x axis and the percent growth from the previous point on the y axis. For a perfect logistic curve this relationship will be linear. So then I fit a line to the resulting points and project out to where the growth rate eventually falls to 0, indicating the total number has plateaued. I take that number as the prediction. 

I assume that the larger the number of cases gets, the less noisy the data is getting, so I weight each example by the number of cases when fitting the linear model.

This model is not likely to work well when the total number is still small, so  am focusing on countries that have reported more than 100 deaths. I am open to adding more countries: just suggest a color and a country and I can add it.

For a good primer on Logistic Growth, see this great [video by 3Blue1Brown](https://www.youtube.com/watch?v=Kas0tIxDvrg)

I will be updating this data daily using the code in this Github repo.

## Caveats:
1. There is likely to be a second increase in cases after the summer. This surge will likely be another logistic curve on top of this one.
2. If there is a huge change in policy or approach to managing the pandemic (people stop social distancing), then the model will most likely underpredict massively. Predictions from this model should never be used to justify ceasing effective preventative measures like social distancing.
3. If there is a huge surge in testing, the model will probably get confused for a few days and then eventually recover.


