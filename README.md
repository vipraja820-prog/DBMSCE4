Project Overview

The system is designed to manage production and quality information for paper mills.

It stores information about:

Paper mills

Production runs

Paper grades

Production dates

Quality metrics

Measured quality values

The application provides a dashboard where users can add records, view database information, and delete records while maintaining relationships between the database tables.

The project uses SQLite3 as the database and Tkinter for the graphical user interface.

Project Objective

The main objectives of this project are:

To create a relational database for managing paper mill production data.

To store paper mill information in a structured database.

To maintain production run records associated with each mill.

To store quality measurements for each production run.

To demonstrate the use of primary keys and foreign keys.

To maintain database integrity using constraints.

To demonstrate SQL JOIN operations.

To implement cascading deletion between related records.

To validate user input before inserting data.

To provide a simple graphical dashboard for database operations.

Features

Add new paper mill records.

Add production run information.

Add quality measurements.

Automatically create a mill profile when a new mill is entered.

Reuse an existing mill using case-insensitive matching.

View all production and quality information.

View individual database tables.

Delete paper mills.

Delete production runs.

Delete quality items.

Automatically delete related records using ON DELETE CASCADE.

Validate user input.

Prevent negative quality measurements.

Prevent invalid numeric values.

Use database transactions for safe record insertion.

Use SQLite foreign-key enforcement.

Include sample data when the database is empty.

Include a database self-test to verify database operations.

Technologies Used

Python

Python is used as the main programming language for developing the application.

SQLite3

SQLite3 is used as the relational database management system.

It stores all the project data in a local database file named:

paper_mill.db

Tkinter

Tkinter is used to create the graphical user interface and dashboard.

SQL

SQL is used for:

Creating tables

Inserting records

Selecting records

Joining tables

Deleting records

Applying constraints

Managing relationships

Python Libraries

The project uses the following Python modules:

sqlite3

tkinter

math

os

sys

datetime

Database Structure

The project contains three main relational tables.

1. Mills

The mills table stores information about paper mills.

Column

Data Type

Description

mill_id

INTEGER

Primary key

mill_name

TEXT

Name of the paper mill

contact_email

TEXT

Contact email

Primary Key

mill_id uniquely identifies every paper mill.

Constraint

mill_name is UNIQUE and NOT NULL.

2. Production Runs

The production_runs table stores information about individual production runs.

Column

Data Type

Description

run_id

INTEGER

Primary key

mill_id

INTEGER

Foreign key

paper_grade

TEXT

Type/grade of paper

run_date

TEXT

Production date

Primary Key

run_id uniquely identifies every production run.

Foreign Key

mill_id references:

mills(mill_id)

This creates a relationship between a paper mill and its production runs.

3. Quality Items

The quality_items table stores quality measurements for production runs.

Column

Data Type

Description

item_id

INTEGER

Primary key

run_id

INTEGER

Foreign key

quality_metric

TEXT

Quality measurement type

measured_value

REAL

Measured quality value

Primary Key

item_id uniquely identifies each quality record.

Foreign Key

run_id references:

production_runs(run_id)

This connects quality measurements with their corresponding production runs.

Database Relationship

The database follows a relational structure:

Mills → Production Runs → Quality Items

One paper mill can have multiple production runs.

One production run can have multiple quality items.

Therefore:

Mills (1) → Production Runs (Many)

Production Runs (1) → Quality Items (Many)

Database Integrity

Database integrity is maintained using several techniques.

Primary Keys

Each table contains a primary key:

mill_id

run_id

item_id

These uniquely identify records.

Foreign Keys

Foreign keys maintain relationships between tables.

production_runs.mill_id references mills.mill_id.

quality_items.run_id references production_runs.run_id.

Foreign Key Enforcement

The project explicitly enables SQLite foreign-key enforcement using:

PRAGMA foreign_keys = ON

This prevents invalid relationships between tables.

NOT NULL Constraints

Important fields cannot contain empty database values.

For example:

mill_name

contact_email

paper_grade

run_date

quality_metric

measured_value

UNIQUE Constraint

The mill_name field is unique, preventing duplicate mill names.

CHECK Constraint

The measured_value field contains:

CHECK (measured_value >= 0)

This prevents negative quality measurements from being stored.

CASCADE Delete

The project uses:

ON DELETE CASCADE

If a paper mill is deleted, its production runs and related quality items are also deleted.

If a production run is deleted, its quality items are automatically deleted.

This prevents orphan records.

SQL JOIN Operation

The project includes a Master Quality View that combines information from multiple tables.

The project uses:

JOIN

LEFT JOIN

to display information such as:

Run ID

Mill Name

Paper Grade

Run Date

Quality Metric

Measured Value

This demonstrates how relational database tables can be combined to produce meaningful information.

Data Validation

Before inserting records, the application validates user input.

It checks that:

Mill name is entered.

Paper grade is entered.

Quality metric is entered.

Measured value is entered.

Measured value is numeric.

Measured value is finite.

Measured value is not negative.

Invalid input generates a validation error instead of being inserted into the database.

Transactions

The project uses database transactions while adding records.

When a production record is added, the required database operations are performed together.

If the operations succeed, they are committed.

This helps maintain database consistency.

Sample Data

When the database is completely empty, the project automatically inserts sample data.

The sample database contains:

3 paper mills

5 production runs

9 quality items

Sample quality metrics include:

Pulp Consistency %

Brightness Index

GSM Weight

The sample data is inserted only when the database has no existing mills.

How to Run the Program

Requirements

Install Python on your computer.

The project uses standard Python libraries, so additional packages are not required.

Method 1: VS Code / Python

Save the Python file as:

paper_mill_dashboard.py

Then open a terminal in the project folder and run:

python paper_mill_dashboard.py

The graphical dashboard will open.

Method 2: Jupyter Notebook

The complete Python code can be pasted into a single Jupyter Notebook cell and executed.

The database file will be created in the current working directory.

Database Self-Test

The project also provides a self-test option.

Run:

python paper_mill_dashboard.py --selftest

This checks:

Database creation

Sample data

Input validation

Existing mill reuse

New mill creation

Record deletion

Cascade deletion

Foreign-key enforcement

Orphan-record prevention

If all tests pass, the console displays:

All database self-tests passed.

Project Workflow

The basic workflow of the application is:

Connect to the SQLite database.

Enable foreign-key enforcement.

Create the required tables if they do not exist.

Insert sample data if the database is empty.

Open the graphical dashboard.

Enter paper mill and production information.

Validate the entered data.

Insert the production and quality records.

View records using database queries.

Delete records when required.

Maintain related records using cascading deletes.

Project Structure

Paper-Mill-Production-Quality-Dashboard/
│
├── paper_mill_dashboard.py
├── paper_mill.db
└── README.md

paper_mill_dashboard.py

Contains the complete Python application, database operations, SQL queries, validation, GUI, and self-test.

paper_mill.db

SQLite database file created by the application.

README.md

Contains project documentation and instructions.

Conclusion

The Paper Mill & Production Run Quality Dashboard is a relational database application that demonstrates how Python can be integrated with SQLite to manage structured production and quality data.

The project demonstrates important DBMS concepts including relational tables, primary keys, foreign keys, constraints, JOIN operations, transactions, validation, cascading deletes, and database integrity through a practical paper manufacturing use case.
