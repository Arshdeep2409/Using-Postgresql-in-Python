# PostgreSQL Sales Data Analysis with Python

## Overview

This project demonstrates how to connect a PostgreSQL database to Python, execute SQL queries, and visualize the results using the pandas library and Matplotlib. The analysis focuses on sales data stored in a PostgreSQL table.

## Project Structure

The repository contains the following:

* `PostgreSql sales project using postgresql in python .ipynb`: A Jupyter Notebook containing the Python code for connecting to the database, querying the sales data, and generating a bar chart.

## Steps Performed

1.  **PostgreSQL Database Setup:**
    * A PostgreSQL database named `sales_data` was created.
    * A table named `sales_data` was created with the following schema:
        ```sql
        CREATE TABLE sales_data (
            Order_ID VARCHAR(20) PRIMARY KEY,
            Customer_ID VARCHAR(20),
            Product VARCHAR(20),
            Quantity INTEGER,
            Price_Per_Unit DECIMAL(5,2),
            Discount DECIMAL(3,2),
            Order_Date DATE,
            Total_Sales DECIMAL(8,4)
        );
        ```
    * Sales data was imported into the `sales_data` table from a CSV file (`Sales.csv`) located at `C:\data files\Sales.csv`. The following PostgreSQL command was used:
        ```sql
        COPY sales_data FROM 'C:\data files\Sales.csv' WITH (FORMAT CSV, HEADER TRUE, DELIMITER ',');
        ```

2.  **Connecting Python to PostgreSQL:**
    * The `psycopg2` library was imported in the Jupyter Notebook to establish a connection with the PostgreSQL database.

3.  **Executing SQL Queries:**
    * A cursor object was created to execute SQL queries.
    * The following SQL query was executed to fetch all data from the `sales_data` table:
        ```sql
        SELECT * FROM sales_data;
        ```

4.  **Loading Data into Pandas DataFrame:**
    * The `pd.read_sql_query()` function from the pandas library was used to execute the SQL query and load the results into a pandas DataFrame named `df`.

5.  **Data Visualization:**
    * A bar chart visualizing the total sales for each product was created using the `plot()` function available in pandas DataFrames.
    * The chart displayed 'product' on the x-axis and 'total_sales' on the y-axis.

## Libraries Used

* `psycopg2`: For connecting to the PostgreSQL database from Python.
* `pandas`: For data manipulation and analysis, including reading SQL query results into a DataFrame and creating the bar chart.
* `matplotlib.pyplot`: (Implicitly used by pandas `plot()` function) For plotting the bar chart.

## Visual Output

The project generated a bar chart showing the total sales for different products.

![Bar Chart of Total Sales per Product](attachment_of_bar_chart.png)
*(Note: Replace `attachment_of_bar_chart.png` with an actual image of the generated bar chart if you include it in your repository.)*

## Setup Instructions

1.  **Install Libraries:**
    ```bash
    pip install psycopg2 pandas matplotlib
    ```

2.  **Set up PostgreSQL:**
    * Ensure you have PostgreSQL installed and running.
    * Create a database named `sales_data`.
    * Create the `sales_data` table using the provided SQL schema.
    * Populate the `sales_data` table by importing your `Sales.csv` file using the `COPY` command or other suitable methods.

3.  **Run the Jupyter Notebook:**
    * Open and run the `PostgreSql sales project using postgresql in python .ipynb` notebook. Make sure to update the database connection details in the notebook if necessary.

## Potential Enhancements

* Implement more sophisticated data analysis and visualization techniques.
* Allow users to specify different queries or data subsets for analysis.
* Create interactive dashboards for exploring the sales data.
* Add error handling and logging to the Python script.
