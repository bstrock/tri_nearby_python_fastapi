<h1>TRI Nearby:  API</h1>
This repo is for the backend component of my final project for Geospatial Web and Mobile Programming.  This API package is designed to read data from US EPA TRI datasets, create a spatial database for the dataset, extract/transform/load relevant data, then serve requests from the app's frontend component to inform user queries and accept user reports about individual sites.

<h2>Link to project demo</h2>

[View a 5 minute overview walkthrough here](https://youtu.be/jYbpUzD-KjI)

[Check out the frontend Swift app repo here](https://github.com/bstrock/tri_nearby_swift_mapkit)

<h2>Tech Stack</h2>

* FastAPI
* SQLAlchemy
* GeoAlchemy2
* asyncio
* pandas
* Docker
* Heroku (deployment)

<h2>Project Features</h2>

* Programatically generated spatial database using SQLAlchemy/GeoAlchemy2
* Fully asynchronous operations using FastAPI and SQLAlchemy's 2.0 style
* Allows users to perform spatial and attribute-based queries to explore TRI sites in their vicinity
* Joined table inheretance structure allows easy loading of attribute tables for storing secondary characteristics
* Complete package- one toolkit to create the database, perform ETL on the data, service queries from the endpoints, and test the API before deployment

<h2>Project Structure and Contents</h2>

```tri_nearby/
├── a.Dockerfile
├── heroku.yml
├── Procfile
├── requirements.txt
├── api/
│       ├── __init__.py
│       └── api.py
├── models/
│       ├── __init__.py
│       ├── enums.py
│       ├── tables.py
│       └── schema.py
├── utils/
│       ├── __init__.py
│       ├── create_spatial_db.py
│       └── tri_data_to_db.py
└── tests/
        ├── __init__.py
        └── test.py
```

`/api` contains the api source code.  uses PostGIS to process spatial queries.

`/models` contains SQLAlchemy database table models and FastAPI schemas, along with a useful utility to define and unpack custom PostgreSQL ENUM types.

`/utils`

  - `create_spatial_db.py` contains a class which offers methods to create databases with PostGIS-enabled spatial datatypes, based on the SQLAlchemy models defined in `models/tables.py`
  - `tri_loader.py` uses pandas and sqlalchemy models to perform ETL operations on TRI Data and imports them into the spatial database

`/tests` Contains an extensive test suite, which provides a continuous integration testing baseline to ensure efficient API development
