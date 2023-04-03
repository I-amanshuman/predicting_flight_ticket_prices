# predicting_flight_ticket_prices
I am trying to analyse the data, find correlation between features, to predict flight ticket prices

This dataset is obtained from Kaggle and it has multiple features, Like duration, stops, departure time, arrival time, etc which are somehow responsible for driving the flight prices

-- Loading the dataset and exploring it --

df.info()
df.isnull().sum()

Creating a copy of the dataset, to proceed ahead with the EDA

![image](https://user-images.githubusercontent.com/77953290/229447523-8c35ed1f-b439-443d-94ad-30dc92fbec8d.png)

- Converting datetime columns to respective data types by defining a function

![image](https://user-images.githubusercontent.com/77953290/229447742-e2986c80-5af1-48e2-a53c-b17f776a77b1.png)

Extracting features from the newly obtained data columns, as new columns in the DataFrame

![image](https://user-images.githubusercontent.com/77953290/229448034-eda00460-e76c-4d80-b4a8-98c60a77a12b.png)

-- Lets create a function which will return the hour and the minute

Departure time Hour and Minute
![image](https://user-images.githubusercontent.com/77953290/229448371-d4f78bf0-41f7-4d5d-a476-5fe7b2813ae2.png)


Arrival time Hour and Minute
![image](https://user-images.githubusercontent.com/77953290/229448591-0989c870-e2d9-42fe-8184-8c784c76e5fc.png)

- Now classifying the data based on Departure hour:
![image](https://user-images.githubusercontent.com/77953290/229449068-a3349c88-1751-46c5-b166-29e5be11ba46.png)

![image](https://user-images.githubusercontent.com/77953290/229449256-7be771bf-ec17-4f53-823a-7ff0eab1ce0a.png)

#Feature engineering duration column, to help our model understand the data in form HH:MM (hours:minutes):
#hint, we look at the annotations, 'h' and 'm' to help segregate the data

def process_duration(x):
    if 'h' not in x:
        x = '0h ' + x
    elif 'm' not in x:
        x= x + ' 00m'
    return x
    
This will help us to split the data in hours and minutes, denoted hy h and m

![image](https://user-images.githubusercontent.com/77953290/229450000-8dd80dcc-340f-41b7-8604-4bb6ae9113ee.png)

Now, lets evaluate the total duration in minutes

![image](https://user-images.githubusercontent.com/77953290/229450185-1f73d0fc-2310-4740-86a9-26bd6a9166ea.png)

Scatter plot, between price and duration
![image](https://user-images.githubusercontent.com/77953290/229450251-5f4a526f-a3f3-49a6-9836-688e85204f7c.png)


#Lets use an lm plot which is a regression and a scatter plot from seaborn library, and looks better!

![image](https://user-images.githubusercontent.com/77953290/229450476-babaa2d9-e28c-46fb-8c7a-fe8057cf1753.png)

-- Bivariate data analysis --

Comparing airlines with price

![image](https://user-images.githubusercontent.com/77953290/229465721-5a8cf96f-00c3-4b87-86b1-cb43fb663c97.png)


Using Violin plots to get distribution and outliers 

![image](https://user-images.githubusercontent.com/77953290/229465853-fdd6e194-b1c0-4338-9126-67e2669de2c5.png)

-- One hot Encoding to change the categorical variables to numerical ones -- 

![image](https://user-images.githubusercontent.com/77953290/229466047-97b52491-b85d-4046-8bd5-a9645a1ee830.png)


-- Detecting outliers using sns boxplot --
![image](https://user-images.githubusercontent.com/77953290/229466255-f9b2db61-b430-4b36-8628-49b8d811741e.png)

-- Imputing the outliers by median, so that the skewness is not impacted by the outliers

![image](https://user-images.githubusercontent.com/77953290/229466484-a7df89e4-3105-4a3c-8c40-4d8abfc097cc.png)


Feature selection from sklearn package, mutual_info_regression

	Importance
Airline	0.980631
Total_Stops	0.792608
source_Delhi	0.517639
total_duration_minutes	0.492751
Duration_hours	0.472158
source_Kolkata	0.466463
Arrival_Time_hour	0.408386
source_Banglore	0.387991
Duration_minutes	0.343591
Arrival_Time_minute	0.341714
Dep_Time_hour	0.341051
Dep_Time_minute	0.253350
journey_month	0.240445
source_Mumbai	0.199007
journey_day	0.195868
source_Chennai	0.129192
journey_year	0.000000

-- Correlation analysis --

![image](https://user-images.githubusercontent.com/77953290/229466768-8dc94d21-5181-4320-b7ff-0dc34ff836f6.png)


![image](https://user-images.githubusercontent.com/77953290/229466847-1f15217a-de8f-4f47-a87b-5b30a19e312e.png)


Let's train the model to get the predicted prices with accuracy

![image](https://user-images.githubusercontent.com/77953290/229467050-0834bb0e-3ca3-4810-89a0-f1cb35901199.png)


Hyperparameter tuning to get a better a R2 score 

![image](https://user-images.githubusercontent.com/77953290/229467229-8a879dfb-bc39-4a49-8d5a-7238515fe05f.png)


New R2 Score:

![image](https://user-images.githubusercontent.com/77953290/229467302-fc80f090-71c0-45e7-ae10-736c752cda79.png)


Thus with the model, we were able to get an R2 of 82%, or in other words, almost 82% of the variance in the data


