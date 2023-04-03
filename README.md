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














