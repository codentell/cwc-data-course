+++
title = "02.  Good Movies Loc 👩‍🎓👨‍🎓"
weight = 2
tags = ["pandas"] 
+++

# Good Movies

In this activity, you will create an application that searches through IMDb data to find only the best movies out there.

## Instructions

* Use Pandas to load and display the CSV provided in `resources`.

* List all the columns in the dataset.

* We're only interested in IMDb data, so create a new table that takes the film and all the columns related to IMDb.

* Filter out only the good movies&mdash;any film with an IMDb score greater than or equal to 7&mdash;and remove the norm ratings.

* Find less popular movies that you may not have heard about&mdash;anything with under 20K votes.

* Finally, export this file to a spreadsheet, excluding the index, so we can keep track of our future watchlist.

## References

[Moving Rating Dataset](https://github.com/fivethirtyeight/data/blob/master/fandango/fandango_score_comparison.csv)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencie
import pandas as pd
# Load in file
movie_file = "./resources/movie_scores.csv"
# Read and display the CSV with Pandas
movie_file_df = pd.read_csv(movie_file)
movie_file_df.head()

# List all the columns in the table
movie_file_df.columns

# We only want IMDb data, so create a new table that takes the Film and all the columns relating to IMDB
imdb_df = movie_file_df[["FILM", "IMDB", "IMDB_norm",
                            "IMDB_norm_round", "IMDB_user_vote_count"]]
imdb_df.head()

# We only like good movies, so find those that scored over 7, and ignore the norm rating
good_movies_df = movie_file_df.loc[movie_file_df["IMDB"] > 7, [
    "FILM", "IMDB", "IMDB_user_vote_count"]]
good_movies_df.head()

# Find less popular movies--i.e., those with fewer than 20K votes
unknown_movies_df = good_movies_df.loc[good_movies_df["IMDB_user_vote_count"] < 20000, [
    "FILM", "IMDB", "IMDB_user_vote_count"]]
unknown_movies_df.head()

# Finally, export this file to a spread so we can keep track of out new future watch list without the index
unknown_movies_df.to_excel("./output/movieWatchlist.xlsx", index=False)
```
{{% /expand%}}