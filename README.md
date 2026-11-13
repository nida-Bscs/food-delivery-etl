# food-delivery-etl
Food Delivery ETL Pipeline

A Python ETL pipeline that reads raw food delivery order data from a CSV file, cleans it, and loads it into Snowflake for analysis.

What it does
Extract
Detects the encoding of the source CSV (chardet).
Re-saves it as UTF-8 and reads it into a pandas DataFrame.
Transform
Reports missing values, duplicate rows and column data types.
Converts any column with "date" in its name to a standard YYYY-MM-DD format.
Converts text columns to a consistent string type.
Load
Saves the cleaned data to a CSV file.
Loads it into a Snowflake table using Snowpark. Each run drops and recreates the table with the latest data.

Every step is logged with timestamps, and file, encoding and database errors are caught and logged.

Tech stack

Python, pandas, chardet, Snowflake (Snowpark), logging
