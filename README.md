# Module-14-Challenge
Module 14 Challenge of FinTech Bootcamp

For this challenge, I attempted to create an algorithmic trading bot that learns and adapts to new data.

## High-Level Steps
### 1 Establish a Baseline Performance
To begin, I took the Starter_Code provided and established a baseline performance for the trading algorithm. After importing the dataset provided I generated trading signals using short and long window SMA values, split the data into training and testing sets, used a SVC classifier to create a support vector machine (SVM) model fitted to the training data, created predictions and plotted the cumulative returns of actual returns vs. strategy returns.

### 2 Tune the Baseline Trading Algorithm
For this step, I took the trading algorithm established and tried to improve it's performance. To do this, I first adjusted the size of the training dataset. Next, I tried adjusting the short and long window values. 

### 3 Evaluate a New Machine Learning Classifier
For the final step, I applied the original trained data and applied it to a second machine learning model. To do this, I initiated a LinearRegression() model and fit the training data to it. Then I made predictions, backtested, and plotted the LR predictions' returns comparing to the actual returns just as I did with the SVM model. 

## Evaluation Report
#### SVM model classification report
                  precision     recall  f1-score   support

       -1.0            0.43      0.04      0.07      1804
        1.0            0.56      0.96      0.71      2288

        accuracy                           0.55      4092
        macro avg      0.49      0.50      0.39      4092
        weighted avg   0.50      0.55      0.43      4092

The SVM model is on 55% accurate overall. It is very good at recalling long position trades (1.0) but very poor at recalling short position trades (-1.0). Furthermore, it is not very precise for short or long positions.


![Actual Returns V  Strategy Returns baseline](https://github.com/JulHendrickson/Module-14-Challenge/assets/81846691/56dd9c21-a1f0-48a9-8146-23253c5aa457)
This model's returns show it underperformed compared to actual returns.

#### SVM model classification report after adjusting SMA and training data
                   precision    recall  f1-score   support

       -1.0            0.57      0.00      0.01      1867
        1.0            0.56      1.00      0.72      2400

        accuracy                           0.56      4267
        macro avg      0.57      0.50      0.36      4267
        weighted avg   0.57      0.56      0.41      4267
        
After applying adjusting the parameters the model performed even better at recalling long position trades (1.0) and even worse at recalling short position trades (-1.0). There were no improvements in precision.


![Actual Returns V  Strategy Returns tuned training](https://github.com/JulHendrickson/Module-14-Challenge/assets/81846691/40766a85-f48d-4912-985f-3fc567031e92)
I found that increasing the size of the training dataset seemed to negatively affect the trading algorithm. So I decreased to one month and saw it performed very similar to the baseline with a slight improvement at the beginning and end of the data period. 


![Actual Returns V  Strategy Returns tuned SMA](https://github.com/JulHendrickson/Module-14-Challenge/assets/81846691/95e3fd18-19c8-4438-88fe-606ed32d92f8)
I found that increasing both SMA windows seemed to negatively affect the trading algorithm. I decreased both and saw the same negative affect. Then, I decided to shorten the short window and lengthen the long window and saw a slight improvement overall. However, It still seemed to remain very consistent with the baseline.

![short_1_long_10_1_month](https://github.com/JulHendrickson/Module-14-Challenge/assets/81846691/38af814e-b2b0-4ee7-bafe-7496b47d2da2)
For the final adjustment, I decreased the training size to one month. Then I set the short and long windows to 1 and 110 days respectively.

#### Linear Regression model classification report
                   precision    recall  f1-score   support

       -1.0            0.44      0.33      0.38      1804
        1.0            0.56      0.66      0.61      2288

        accuracy                           0.52      4092
        macro avg      0.50      0.50      0.49      4092
        weighted avg   0.51      0.52      0.51      4092
        
This model was better at recalling short position trades (-1.0) and more precise as well. It was not as good at recalling long position trades (1.0) nor as precise. 



## Conclusion

These models would not produce consistent winning trades. More data and further adjusting of the algorithm is needed before going live with this trading bot.
