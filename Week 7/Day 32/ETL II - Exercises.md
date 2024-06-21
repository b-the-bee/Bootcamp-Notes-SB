#data-engineering #python 

## ETL Exercise

The ETL Process will be used to carry out the following exercise in Data Analysis.

We have a set of customer sales data that we want to extract information from.

Needs Docker or Podman running a postgres container that we can use to save the data - see also the [Docker](https://www.odwebp.svc.ms/docker/) or [databases](https://www.odwebp.svc.ms/databases/) or [databases-sot](https://www.odwebp.svc.ms/databases-sot/) sessions.

- The [docker-compose.yml](https://www.odwebp.svc.ms/handouts/docker-compose.yml) used here is the same as for the above mentioned [databases](https://www.odwebp.svc.ms/databases/) session.

## Initial setup

1. Setup mysql database with docker
    1. Change directory to handouts by running `cd handouts`
    2. Spin up a new Adminer container with `docker compose up -d` in the handouts directory
    3. In the browser go to [http://localhost:8080](http://localhost:8080/) to open the Adminer UI
        1. Change the database type dropdown to "MySQL"
        2. Enter Server `db`, Username `root` and Password `password` to log in
        3. You can use this UI to check any SQL you want to run
2. Create a 'test' database in your MySQL by running the sql `CREATE DATABASE test;`
3. Create virtual environment with python by running `python3 -m venv .venv` (Mac / Unix) or `py -m venv .venv` (Windows)
4. Activate the virtual environment with `source .venv/bin/activate` (Mac / Unix) or `.venv\Scripts\activate.bat` (Windows)
5. Install the required libraries by running `python3 -m pip install -r requirements.txt` (Mac / Unix) or `py -m pip install -r requirements.txt` (Windows)

### Task

Write a python script that executes the below steps. For the transformation you can use SQL queriers with pymysql.

Make sure to utilise `solution_start.py` which sets up the relevant tables in the database, using `sql_utils.py`, and splits the code into Extract, Transform, and Load stages of an ETL Pipeline.

### Extract

1. Extract all the data from the `sales_data.csv`. The columns for the csv are `customer_id`, `purchase_date`, `purchase_amount` and `product_id`.

### Transform

1. Clean that data (minimum requirement is to remove any rows that contain null cells).
2. Filter data for the period 1 December 2020 - 5 December 2020
3. Calculate each customer's total spend
4. Calculate each customer's average spend
5. Calculate how many times each customer has purchased a specific item

### Load

1. Load the results into a database set up by `sql_utils.py`, you will be able to have a look at the DB schema from the queries in that file.

### Analyse

1. What does the data in the tables tell you about the different customers purchasing habits?