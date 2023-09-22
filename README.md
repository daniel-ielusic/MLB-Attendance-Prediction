# MLB Attendance Prediction and Promotion Analysis

## Project Overview
* Created a tool to predict attendance at Major League Baseball games (MAE ~ 3700) in order to help teams understand factors that drive attendance, better forecast demand, and optimize their promotional schedules.
* Collected attendance data as well as team stats from the 2012 Major League Baseball season.
* Engineered features by combining my domain knowledge with extensive exploratory data analysis to identify hidden relationships in the data, further improving the performance of the model's predictions and interpretability.
* Optimized Linear Regression and Random Forest Regression models to maximize performance. 
* Applied GINI importance and SHAP values to assess feature importance and make specific recommendations to MLB teams' marketing and ticketing departments.


## Data
* attendance.csv: attendance data from 2012 MLB season, containing information such as the home team, visiting team, day of week, weather, promotions, and attendance. I acquired this from the book [*Marketing Data Science: Modeling Techniques in Predictive Analytics with R and Python*](https://www.amazon.com/Marketing-Data-Science-Techniques-Predictive/dp/0133886557) by Thomas Miller.
* batting.xlsx, pitching.xlsx, standings.xlsx: Team-level statistics related to offensive, pitching and overall performance in the 2012 season, which was combined with the bobbleheads dataset to better predict attendance. This data was collected from the popular baseball statistics website [Fangraphs.](https://www.fangraphs.com/)

## File Structure
* data folder: contains the datasets I collected as well as a cleaned dataset for modeling.
* code folder: contains two notebooks:
  * Data Importation, Cleaning, and Exploratory Analysis: In this file, I join the datasets together, explore relationships in the data, and create new features to better predict attendance.
  * Model Building: In this file, I build linear regression and random forest regression models, optimize their performance, evaluate results and assess feature importance.
  * **Note:** Both of these files are in notebook format and integrate notes and analysis throughout!
 
## Methodology
### Exploratory Analysis and Data Preprocessing
Before diving into the model-building process, I completed extensive data preprocessing to enhance predictions and better understand the dataset.
1. *Data Cleaning:* This process was relatively simple since there were no missing values, but I joined the data from disparate sources together and removed 4 games with extreme temperature outliers.
2. *Feature Engineering:* Throughout the exploratory data analysis process I continuously created new features to better capture factors that affect attendance. Please reference the Analysis notebook for the full methodology, but I provide two examples below:
  a. To limit overfitting while capturing the value of the day of week variable, I created a feature indicating whether a game was played on a Friday through Sunday, as the boxplot below shows that these games had higher overall attendance.
  b. I created a variable to indicate whether a game was played on a holiday other than Labor Day, as these games often led to larger crowds as show in Figure 2.
3. *Feature Scaling:* I normalized quantitative features in order to ensure they are on the same scale and more accurately assess feature importance.
4. *One-Hot Encoding:* I one-hot encoded categorical data to convert these features into a suitable format for machine learning.

### Model Building:
1. *Train-Test-Split:* I used 70% of the data as a training set and 30% as a test set to evaluate model performance.
2. *Hyperparameter Tuning:* After building a random forest regression pipeline, I used a grid search to find the ideal number of trees in the forest, maximum depth of each tree, minimum number of samples to split a node, minimum number of samples required for a leaf node, and maximum number of features.
3. *Model Evaluation and Selection:* I used mean absolute error and R<sup>2</sup> to evaluate model performance and decided to use the random forest model over the linear regression model. The best-performing random forest regression model had the following metrics:
   * Mean Absolute Error: 3704
   * R<sup>2</sup>: 0.725
4. *Feature Importance:* To determine the relative importance of each feature in the models, I calculated the coefficients for the linear regression model, as well as GINI importance and SHAP values for the random forest regression. Figure 3 shows the importance rank of each feature by method.

Figure 1: Attendance by Day of Week

![Screenshot 2023-09-22 at 10 25 24 AM](https://github.com/daniel-ielusic/MLB-Attendance-Prediction/assets/92276875/69442ac0-1201-47fd-b35e-b60f37e2cc57)

Figure 2: Attendance on Holidays

![Screenshot 2023-09-22 at 10 28 57 AM](https://github.com/daniel-ielusic/MLB-Attendance-Prediction/assets/92276875/f579f248-2156-4818-805c-aa177f7d2492)

Figure 3: Feature Importance by Three Primary Methods

![Screenshot 2023-09-22 at 10 42 09 AM](https://github.com/daniel-ielusic/MLB-Attendance-Prediction/assets/92276875/44a6a6ca-4fe8-4066-a765-1398391014d7)

## Key Insights and Activation
For a more detailed breakdown, please see the comments at the bottom of the Model Building notebook. However, here is a high-level overview of the results:
1. The model is able to predict attendance with an average error of 3,700. Teams can use this information to forecast demand for concessions, effectively time promotions and identify periods of high fan engagement.
2. Teams should look to capitalize revenue in games against high-powered offenses, as these are safe bets to bring in large crowds.
3. Teams should prioritize bobblehead promotions over others, as they lead to the greatest uplift in attendance.
4. Given the fact that weekend games have significantly greater demand than weekday games when accounting for other factors, ticketing departments should consider alternative strategies, bundles, and reduced prices to sell Monday-Thursday tickets.

## Next Steps

While I have completed the initial objectives of this project, there are plenty of opportunities to further improve the quality of analysis moving forward. Beyond continuing to refine existing code and visualizations, I have highlighted a few of these areas below:

1. Look into building models for each individual team for more specific analysis. This could be difficult with only one season's worth of data, but is certainly possible if more data becomes available.
2. Train the model on weekday vs. weekend games and observe the relative effect of promotions in each situation. This could help the marketing department best identify games to run promotions.
3. Analyze promotions that resulted in the greatest uplift in promotions, either through Shapley Values or residual analysis, to further identify the best opportunities to run promotions.

## Contact Information

If you have any comments or ideas for improvement, please email me at dielusic@nd.edu or message me on [LinkedIn.](https://www.linkedin.com/in/daniel-ielusic/)
