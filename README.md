# Movies-ETL

## Project Overview
The purpose of this project is to be able to read in movie and ratings data, perform an extract-transform-load process on it, and then upload the cleanded data to a SQL Database.  This code can be run on a determined schedule, accepting in the three updated files. 


##  Resources
The following resources were used to complete this analysis:
- Input Data Sources:  Wikipedia (movie data) and Kaggle (movie and ratings data)
- Output Source:  movie_data (Database)
- Software:  Jupyter Notebook, PostgreSQL, Visual Studio Code


## Project Summary
### Extract
The data is extracted from the following 3 files:
- wikipedia-movies.json (json file containing movie data from the wikipedia sidebar)
- movies_metadata.csv (movie data downloaded from Kaggle)
- ratings.csv (ratings data downloaded from Kaggle/MovieLens)

    
### Transform  
The following functions are run to transform/clean the data:
1. Clean Wikipedia data:
    - Combine all "alternate titles" type columns into one column
    - Update column names 
    - Extract imdb_id from imdb_link
    - Drop imdb_id duplicates
    - Drop columns that contain a majority of null values
    - Clean the "Box office" values to be more consistent and convert to float datatype
    - Clean "Budget" values to be more consistent and convert to float datatype
    - Clean "Release date" values to be more consistent and convert to datatime format
    - Clean "Running time" values to be more consistent

2. Clean Movie-Metadata:
    - Drop movies labeled as "Adult"
    - Update "Budget", "ID", and "Popularity" columns to numeric datatypes.
    - Update "Release Date" to datetime format.

3. Merge Wikipedia and Movie Metadata:
    - Delete duplicate columns
    - Fill in missing data
    - Filter the database on the columns to keep
    - Rename columns

4. Merge ratings data:
    - Calculate counts by movie and rating 
    - Merge ratings counts with movies data

### Load
The data is uploaded to the movie_data database.  
- The cleaned and merged movie data is uploaded to the "movies" table.  If the table already exists, it will be dropped during the upload and recreated.
- The ratings data is uploaded to the "ratings" table. 
Note:  Due to its large size, if the table already exists it should be dropped prior to initiating the upload.




