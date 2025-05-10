# Walmart Time-Series Forecasting using ARIMA and Exponential Smoothing
*This project was made under **AICTE-IBM Cloud (Edunet Foundation)** internship*

## Problem Statement

Walmart is a renowned retail corporation that operates a chain of hypermarkets. Here, Walmart
has provided a data combining of 45 stores located in different regions including store
information and monthly sales. Each store contains a number of departments and the task is to
predict the department-wise sales for each store. The data is provided on weekly basis. In
addition, Walmart runs several promotional markdown events throughout the year. These
markdowns precede prominent holidays, the four largest of which are Christmas, Thanksgiving,
Super bowl and Labor Day. The weeks including these holidays are weighted five times higher in
the evaluation than non-holiday weeks. Part of the problem is modelling the effects of
markdowns on these holiday weeks in the absence of complete/historical data.

<p align="center">
<img src="https://github.com/sanyabhanot/Walmart-Sales-Forecasting/assets/111521883/a57d2cdd-0aaf-489d-a92d-deea9354891c">
<p>
  
## Proposed Solution

The proposed system aims to address the challenge of predicting department-wise sales for each store on a weekly basis. This involves leveraging data
analytics and machine learning techniques to forecast demand patterns accurately. The solution will consist of the following components:

1. **Data Collection**
- Gather historical data on department-wise sales, including time, date, location, and other relevant factors.
- Utilize real-time data sources, such as events, and holidays, to enhance prediction accuracy.

2. **Data Preprocessing**
- Clean and preprocess the collected data to handle missing values, outliers, and inconsistencies.
- Feature engineering to extract relevant features from the data that might impact bike demand.

3. **Machine Learning Algorithm**
- Implement a machine learning algorithm, such as a time-series forecasting model , ARIMA, to predict weekly sales based on historical patterns.
- Consider incorporating other factors like month of the year, day of the week, and special events to improve prediction accuracy.

4. **Deployment**
- Develop a user-friendly interface or application that provides real-time predictions for weekly sales at different dates..
- Deploy the solution on a scalable and reliable platform, considering factors like server infrastructure, response time, and user accessibility.

5. **Evaluation**
- Assess the model's performance using appropriate metrics such as Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), or other relevant
metrics.
- Fine-tune the model based on feedback and continuous monitoring of prediction accuracy.

## Algorithm and Deployment

**Algorithm Selection**

ARIMA is a popular method of modeling time series, because of its flexibility and generalizability. The primary goal of this project was to
examine a method to use fewer than 100 non-seasonal ARIMA models to generate weekly forecasts for over 3000 individual series, over the
span of one year.

**Data Input**

There are 3 Datasets :
1. **Stores.csv**
- Store: The store number. Range from 1–45.
- Type: Three types of stores ‘A’, ‘B’ or ‘C’.
- Size: Sets the size of a Store would be calculated by the no. of products available in the particular store ranging from 34,000 to 210,000.
  
**primary key is Store**
  
2. **Sales.csv**
It containes five features:
- Store: integer values to identify individual stores.
- Dept: integer values to identify specific departments (not unique per store).
- Date: strings of the form yyyy-mm-dd, meant to indicate the week of month and year.
- Weekly_Sales: floats giving the sales recorded for that week, in dollars.
- IsHoliday: Boolean (True/False) for if a major holiday occurred during that week.
  
**primary key is a combination of (Store,Dept,Date)**

3. **Features.csv**:
- Temperature: Temperature of the region during that week.
- Fuel_Price: Fuel Price in that region during that week.
- MarkDown1:5 : Represents the Type of markdown and what quantity was available during that week.
- CPI: Consumer Price Index during that week.
- Unemployment: The unemployment rate during that week in the region of the store.
  
**primary key here is a combination of (Store,Date)**

**Training Process**

The algorithm is trained using historical data using techniques such as feature selection or feature importance determining the model will train better with the whole dataset or by dropping specific columns.

**Prediction Process**

Automated selection was achieved by iterating over each series, and fitting each to all order combinations, with values from zero to two. The models were evaluated, and orders selected, using Akaike Information Criterion (AIC). The process is made more accurate by using Exponential Smoothing.

## Results

- **Graph showing prediction of weekly sales using auto-Arima model. The prediction lines are not that aligned to the test data**
![image](https://github.com/sanyabhanot/Walmart-Sales-Forecasting/assets/111521883/cced4c65-6e28-4c44-ac5b-783a5575656a)

- **Diagnostics of auto Arima model**
  ![image](https://github.com/sanyabhanot/Walmart-Sales-Forecasting/assets/111521883/75649a0c-60a6-483f-89cf-35947a5aa926)

- **Graph showing prediction of weekly sales using Exponential Smoothing. The lines are more aligned to the testing data**
![image](https://github.com/sanyabhanot/Walmart-Sales-Forecasting/assets/111521883/1e249bfe-cde5-47d7-a2c4-eedf85a7a0d4)

- **Model Deployment using Streamlit**
  
  ![image](https://github.com/sanyabhanot/Walmart-Sales-Forecasting/assets/111521883/6c4ea4ed-069c-4514-aa5c-a5c724a62da2)

## Conclusion

- In conclusion, some departments has higher sales, on average others can be best. It shows us, some departments has effect on sales on some seasons like Thanksgiving.
- It is same for stores, means that some areas has higher seasonal sales.
- Stores has 3 types as A, B and C according to their sizes. Almost half of the stores are bigger than 150000 and categorized as A. According to type, sales of the stores are changing.
- As expected, holiday average sales are higher than normal dates.
- Top 4 sales belongs to Christmas, Thanksgiving and Black Friday times. Interestingly, 22th week of the year is the 5th best sales. It is end of May and the time when schools are closed.
- Christmas holiday introduces as the last days of the year. But people generally shop at 51th week. So, when we look at the total sales of holidays, Thanksgiving has higher sales between them which was assigned by Walmart. But, when we look at the data we can understand it is not a good idea to assign Christmas sales in data to last days of the year. It must assign 51th week.
- January sales are significantly less than other months. This is the result of November and December high sales. After two high sales month, people prefer to pay less on January.
- CPI, temperature, unemployment rate and fuel price have no pattern on weekly sales.

## Future Scope

- Data will be made more stationary with different techniques.
- More detailed feature engineering and feature selection will be done.
- More data can be found to observe holiday effects on sales and different holidays will be added like Easter, Halloween and Come Back to School times.
- Markdown effects on model will be improved according to department sales.
- Different models can be build for special stores or departments.
- Market basket analysis can be done to find higher demand items of departments.
