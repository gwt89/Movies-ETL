# Movies-ETL
## Project Overview
The goal of this project is to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables. The code from the module will have to be refactored to create one function that takes in the three files; Wikipedia data, Kaggle metadata, and MovieLens rating data. This will then be used to perform the ETL process by adding the data to a PostgreSQL database.

## Resources
Data Source: wikipedia-movies.json, movies_metadata.csv, ratings.csv
Software: pgAdmin 4 v6.8, Jupyter Notebook, PostgreSQL

## Results
Deliverable 1: Write an ETL Function to Read Three Data Files

An ETL function is written to read in the three data files.

The function converts the Wikipedia JSON file to a Pandas DataFrame, and the DataFrame is displayed in the ETL_function_test.ipynb file.

![wiki_movies_df](https://user-images.githubusercontent.com/105949411/182452978-470dc197-94e7-4f37-8a5a-0a070639f447.png)

The function converts the Kaggle metadata file to a Pandas DataFrame, and the DataFrame is displayed in the ETL_function_test.ipynb file.

![kaggle_metadata](https://user-images.githubusercontent.com/105949411/182453029-4d80f3ef-c1a2-433f-87b7-de71259e1b52.png)

The function converts the MovieLens ratings data file to a Pandas DataFrame, and the DataFrame is displayed in the ETL_function_test.ipynb file.

![ratings](https://user-images.githubusercontent.com/105949411/182453061-7ec8cb95-c7c5-4811-a5e2-9add43aa1b69.png)

Deliverable 2: Extract and Transform the Wikipedia Data

The TV shows are filtered out, and the wiki_movies_df DataFrame is created.
A try-except block is used to catch errors while extracting the IMDb IDs with a regular expression and dropping duplicate IDs.
The extraction and transformation of the Wikipedia data in the ETL function does the following:
A list comprehension is used to keep columns with non-null values.
The non-null box office data is converted to string values using the lambda and join functions.
A regular expression is used to match the six elements of "form_one" of the box office data.
A regular expression is used to match the three elements of "form_two" of the box office data.
The following columns are cleaned in the Wikipedia DataFrame:
The box office column
The budget column
The release date column
The running time column

![wiki_movies_df pg 1](https://user-images.githubusercontent.com/105949411/182454217-42642c4c-8181-432c-861c-1c67491610bb.png)

![wiki_movies_df 2nd page](https://user-images.githubusercontent.com/105949411/182454237-dd53fa7c-054b-430a-b7cb-72e098eac106.png)

The cleaned Wikipedia data is converted to a Pandas DataFrame, and the DataFrame is displayed in the ETL_clean_wiki_movies.ipynb file.

![wiki_movies_df correct](https://user-images.githubusercontent.com/105949411/182454271-2dcc8041-fd27-483c-9ffd-e2ceda7374aa.png)

Deliverable 3: Extract and Transform the Kaggle data

The extraction and transformation of the Kaggle metadata using the ETL function does the following:
The Kaggle metadata is cleaned.
The Wikipedia and Kaggle DataFrames are merged.
The following is performed on the merged Wikipedia and Kaggle DataFrames to create the movies_df:
Unnecessary columns are dropped.
A function is used to fill in the missing Kaggle data.
The movies_df DataFrame is filtered to keep specific columns.
The movies_df DataFrame columns are renamed.
The extraction and transformation of the MovieLens ratings data using the ETL function does the following:
The ratings counts are cleaned.
The movies_df DataFrame is merged with the cleaned ratings DataFrame to create the movies_with_ratings_df DataFrame.
The empty values in the movies_with_ratings_df DataFrame are filled with “0”.
The movies_with_ratings_df and the movies_df DataFrames are displayed in the ETL_clean_kaggle_data.ipynb file.

![movies_df](https://user-images.githubusercontent.com/105949411/182455113-eb4c03b2-89e2-44a3-bf79-7b6e5d90e30f.png)

![movies_with_ratings_df](https://user-images.githubusercontent.com/105949411/182455137-9098d00a-c42a-473d-be8b-cbbdf297d712.png)

Deliverable 4: Create the Movie Database

The data from the movies_df DataFrame replaces the current data in the movies table in the SQL database, as determined by the movies_query.png.

![movies_query](https://user-images.githubusercontent.com/105949411/182455441-abe433d5-d2c2-4e88-ac43-186d92ec396a.png)

The data from the MovieLens rating CSV file is added to the ratings table in the SQL database, as determined by the ratings_query.png.

![ratings_query](https://user-images.githubusercontent.com/105949411/182455468-fc4900f7-7c10-4d45-82f5-125d9488ff75.png)

The elapsed time to add the data to the database is displayed in the ETL_create_database.ipynb file.
