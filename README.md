# Aviation ETL Project

# For this project, I created a pipeline for data exported from The Bureau of Transportation Statistics. There were three aviation datasets in scope: Finances, Carrier Information, and On-Time Flights. Each dataset contained 1000 to 7 million rows of data in an excel format.

![image](https://user-images.githubusercontent.com/80182167/172061813-5f932c50-940a-4cf3-872d-bc5646d9cfc5.png)

# I used Python and Pandas to clean the data to remove all columns with over 50% of its values missing. This significantly reduced the number of columns in the On-Time dataset. Then I removed rows with missing values.

# That data was exported to excel files and loaded to Azure PostgreSQL with a connection to pgAdmin. I used pgAdmin to understand the data structure and normalize the data to second normal form. With 2NF, I separated any attributes not dependent on the primary key. This resulted in the final database structure having 9 tables instead of the original 3.
