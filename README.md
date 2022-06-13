# Aviation ETL SQL Database Project

I explored aviation data from the Bureau of Transportation Statistics to upload to Azure Database for PostgreSQL. This project study looked at data cleaning methods using pandas data frames, Azure cloud computing with the relational database PostgreSQL, and data normalization techniques in practice.

![image](https://user-images.githubusercontent.com/80182167/172061813-5f932c50-940a-4cf3-872d-bc5646d9cfc5.png)

Hardware and Software:

All programs were run on a Windows 10 64-bit operating system. The Azure Database for PostgreSQL consisted of a flexible server with 2 vCores, 8 GiB RAM, 128 GiB storage. PostgreSQL 13 was used for this project with Graphical User Interface pgAdmin 4 connected to Azure PostgreSQL.

![image](https://user-images.githubusercontent.com/80182167/173336560-47e53e28-c2d2-44be-9f6c-4d58124e418a.png)

How the Code Works:

First, the zipped csv files were downloaded to my local Windows machine from the Bureau of 
Transportation Statistics website. Python was used to unzip to my project folder and combine read those files into one pandas data frame for cleaning. For the initial structure of the 3 data sets, the Financials dataset had 79 columns and about 1000 rows, the Carriers dataset had 36 rows and over 1 million rows, and the On-Time dataset had 5 years with 110 columns and 5-7 million rows each. To clean this data, I removed columns that had over 50% of its values missing and then removed all rows containing missing values. 

![image](https://user-images.githubusercontent.com/80182167/173338640-da349dbe-2c78-4f81-a590-cfe3c22d4996.png)

Once that was complete, I wrote to a csv file. The Financials and Carriers dataset were small enough to process and write to their own files. The On-Time dataset needed to be combined and processed by year because of the larger number of rows ranging from 5-7 million each. Then I connected Azure PostgreSQL with pgAdmin and uploaded the data.

![image](https://user-images.githubusercontent.com/80182167/173336635-87b15730-63fd-4cfc-8a74-4252f1399ea9.png)

![image](https://user-images.githubusercontent.com/80182167/173338490-263f3053-c296-4c74-b093-c0d7f1188acb.png)

Then I looked at normalizing the dataset. This image shows the table structure before normalization. 

![image](https://user-images.githubusercontent.com/80182167/173337853-93909a3b-ff12-4bd9-83b3-770c17005e5a.png)

The data was normalized to first normal form, or 1NF, where the primary keys are assigned in red. 

![image](https://user-images.githubusercontent.com/80182167/173338004-686c7bf4-f1ed-4171-989f-5e9d7f0445f7.png)

The next image shows the data in second normal form where any data that did not depend on the primary keys were separated to a new table and foreign keys were assigned in green.

![image](https://user-images.githubusercontent.com/80182167/173338182-41db59a7-171c-4ef3-9492-5f9e0e433062.png)

I considered normalizing to third normal form, but this would have resulted in many more tables and many more joins for the Financials dataset. This table has several total columns that do not depend on primary keys so those would all need to have their own tables in third normal form. For this reason, the highest level of normalization is second normal form.


# Queries:

This query calculates the average departure delays in minutes and average arrival delays in minutes for each airline. The screenshot shows the top 10 entries for lowest average arrival delay: Hawaiian Airlines, Horizon Air, Alaska Airlines, Delta Airlines, Southwest Airlines, Endeavor Air, Republic Airlines, Envoy Air, American Airlines, and PSA Airlines.

![image](https://user-images.githubusercontent.com/80182167/173338752-f730b558-9ded-436b-837c-eda634d3f105.png)


This query shows the highest total assets per year for each carrier. American Airlines has had more total assets in all years 2017-2021 than the other airlines with 2019 being the largest total asset year.

![image](https://user-images.githubusercontent.com/80182167/173338796-552606f6-1dc1-4355-ac8d-226135c667a7.png)
