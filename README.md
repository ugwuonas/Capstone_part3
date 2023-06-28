# Capstone_part3

## Access to PostgreSQL Data Migration

This script migrates data from an Access database to a PostgreSQL database. It utilizes the `pyodbc` library to connect to the Access database and the `psycopg2` library to connect to the PostgreSQL database.

## Prerequisites

- Python 3.x
- Access database file (`.mdb` or `.accdb`)
- PostgreSQL database server
- Required Python libraries: `pyodbc`, `psycopg2`

## Setup

1. Install the required Python libraries:
   pip install pyodbc psycopg2
2. Update the file path of the Access database in the script:
      access_db_file = r"<path_to_access_database>"
      Replace <path_to_access_database> with the actual file path of your Access database.

3. Update the connection details for the PostgreSQL database in the script:
      pg_conn = get_pg_connection('<host>', '<database>', '<user>', '<password>'
      Replace <host>, <database>, <user>, and <password> with your PostgreSQL server details.

4. Run the script:
The script will connect to the Access database, retrieve data from the 'Wpi Data' table, create a corresponding table in the PostgreSQL database, and load the data.

## Notes

The script assumes that the table in the Access database is named 'Wpi Data'. If your table has a different name, modify the access_query variable accordingly.
The script dynamically creates a table in the PostgreSQL database based on the column names and data types retrieved from the Access database. The data type mapping dictionary (data_type_mapping) is used to map Access data types to PostgreSQL data types. Adjust the dictionary if needed.
Ensure that you have appropriate read and write permissions for both the Access and PostgreSQL databases.
