# Food Delivery ETL Pipeline

A Python ETL pipeline that reads raw food delivery order data from a CSV file, cleans it, and loads it into Snowflake for analysis.

## What it does

1. **Extract**
   - Detects the encoding of the source CSV (`chardet`).
   - Re-saves it as UTF-8 and reads it into a pandas DataFrame.
2. **Transform**
   - Reports missing values, duplicate rows and column data types.
   - Converts any column with "date" in its name to a standard `YYYY-MM-DD` format.
   - Converts text columns to a consistent string type.
3. **Load**
   - Saves the cleaned data to a CSV file.
   - Loads it into a Snowflake table using Snowpark. Each run drops and recreates the table with the latest data.

Every step is logged with timestamps, and file, encoding and database errors are caught and logged.

## Tech stack

Python, pandas, chardet, Snowflake (Snowpark), logging

## Setup

1. Install the dependencies:

   ```bash
   pip install pandas chardet snowflake-connector-python snowflake-snowpark-python
   ```

2. Set your Snowflake credentials as environment variables (never put them in the code):

   ```powershell
   $env:SNOWFLAKE_USER="your_user"
   $env:SNOWFLAKE_PASSWORD="your_password"
   $env:SNOWFLAKE_ACCOUNT="your_account"
   ```

3. In `food_delivery_etl.py`, update the three file paths (`input_file_path`, `output_file_path`, `transformed_file_path`) to match your machine, and check the warehouse, database, schema and table names.

4. Run it:

   ```bash
   python food_delivery_etl.py
   ```

## Notes

- The source CSV is not included in this repository.
- Credentials are read from environment variables so they are never stored in the code.

## Author
Nida Omair · LinkedIn

Nida Omair · [LinkedIn](https://linkedin.com/in/nida07090-omair)
