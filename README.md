# WPI Data Analysis
The World Port Index contains the location and physical characteristics of, and the facilities
and services offered by major ports and terminals worldwide. I migrated the World Port Index data from an old
Access database to a modern relational database management system (PostgreSQL) and created data marts from analysis of the data.

This repository contains code snippets for analyzing port data using a PostgreSQL database which include:
- ### EL_pipeline.ipynb
  This script migrates data from an Access database to a PostgreSQL database. It utilizes the `pyodbc` library to connect to the Access database, the `os` library, and the `psycopg2` library to connect to the PostgreSQL database.

- ### question1.ipynb
  This script executes an SQL query that retrieves the nearest ports to Singapore's JURONG ISLAND port. It utilizes the `psycopg2` library to connect to the PostgreSQL database and the `os` library.
  
- ### question2.ipynb
  This script executes an SQL query that determines the country with the largest number of ports with a cargo_wharf. It utilizes the `psycopg2` library to connect to the PostgreSQL database and the `os` library.
  
- ### question3.ipynb
  This script executes an SQL query that determines the nearest port with provisions, water, fuel oil, and diesel based on given coordinates. It utilizes the `psycopg2` library to connect to the PostgreSQL database and the `os` library.
  


## Prerequisites
Before running the code, ensure that the following prerequisites are met:
- Python 3.x is installed on your system.
- PostgreSQL database server
- Required packages(Python libraries: `pyodbc`, `psycopg2`) are installed. You can install them using pip.


## Instructions
To interact with the Access database, follow these steps:
1. Ensure that you have an Access database file (.mdb or .accdb).
2. Connect to the Access database:
   - Modify the get_access_connection function parameter access_conn_str to point to your Access database file.
   - Call the get_access_connection function to establish a connection to the Access database.
3. Connect to the PostgreSQL database:
   - Modify the get_pg_connection function parameters if necessary (host, database, user, password).
   - Call the get_pg_connection function to establish a connection to the PostgreSQL database.
4. Execute the code to perform the desired operations, such as importing data, querying, etc.
5. Close the cursors and connections:
   - Close the Access cursor and connection using access_cursor.close() and access_conn.close().
   - Close the PostgreSQL cursor and connection using pg_cur.close() and pg_conn.close().
     
To import data from the Access database to PostgreSQL, the code performs the following steps:
1. Connect to the Access database (as described in the previous section).
2. Connect to the PostgreSQL database (as described in the previous section).
3. Execute a SELECT query on the Access database to retrieve the desired data.
4. Create a table in the PostgreSQL database dynamically:
   - Fetch the column names and data types from the Access cursor description.
   - Create a table with corresponding columns and data types in PostgreSQL.
5. Insert the retrieved data into the dynamically created PostgreSQL table.
6. Commit the changes to the PostgreSQL database.
7. Close the cursors and connections (as described in the previous section).

To query the nearest ports based on given coordinates, the code performs the following steps:
1. Connect to the PostgreSQL database (as described in the previous section).
2. Execute an SQL query to calculate the distances between the given coordinates and all other ports.
- Modify the SQL query if necessary to match the column names in your database.
3. Create a table in the PostgreSQL database to store the nearest ports.
4. Retrieve the desired columns (port name and distance) from the result set and insert them into the nearest ports table.
5. Commit the changes to the PostgreSQL database.
6. Close the cursor and connection (as described in the previous section).

To determine the country with the largest number of ports with a cargo wharf, the code performs the following steps:
1. Connect to the PostgreSQL database (as described in the previous section).
2. Execute an SQL query to count the number of distinct ports with a cargo wharf for each country.
3. Create a table in the PostgreSQL database to store the results.
4. Retrieve the desired columns (country and port count) from the result set and insert them into the table.
5. Commit the changes to the PostgreSQL database.
6. Close the cursor and connection (as described in the previous section).
   
To find the nearest port with provisions, water, fuel oil, and diesel based on the given coordinates, the code performs the following steps:

1. Connect to the PostgreSQL database (as described in the previous section).
2. Specify the latitude and longitude values.
3. Execute an SQL query to find the nearest port with the required supplies.
- Modify the SQL query if necessary to match the column names in your database.
4. Create a table in the PostgreSQL database to store the result.
5. Retrieve the desired columns (country, port name, latitude, and longitude) from the result set and insert them into the table.
6. Commit the changes to the PostgreSQL database.
7. Close the cursor and connection (as described in the previous section).
  
### Notes

The script assumes that the table in the Access database is named 'Wpi Data'. If your table has a different name, modify the access_query variable accordingly.
The script dynamically creates a table in the PostgreSQL database based on the column names and data types retrieved from the Access database. The data type mapping dictionary (data_type_mapping) is used to map Access data types to PostgreSQL data types. Adjust the dictionary if needed.
Ensure that you have appropriate read and write permissions for both the Access and PostgreSQL databases.

## Troubleshooting
If you encounter any issues or errors while running the code, consider the following:
- Ensure that the PostgreSQL server is running and accessible.
- Verify that the PostgreSQL credentials and database details are correct.
- Check your internet connection and ensure that you can access the file URL.
- Make sure you have the necessary permissions to read and write files and access the database.

## Disclaimer
This code is provided as-is without any warranties. Use it at your own risk. The author is not responsible for any damages or data loss caused by running this code.

