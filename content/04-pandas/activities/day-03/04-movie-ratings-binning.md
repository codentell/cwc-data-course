+++
title = "04.  Movie Ratings Binning  👩‍🎓👨‍🎓"
weight = 4
tags = ["pandas"] 
+++

# Binning Movies

In this activity, you will test your binning skills by creating bins for movies based on their IMDb user vote count.

## Instructions

* Read in the CSV file provided, and print it to the screen.

* Find the minimum "IMDB user vote count" and maximum "IMDB user vote count".

* Using the minimum and maximum "votes" as a reference, create 9 bins to slice the data into.

* Create a new column called "IMDB User Votes Group", and fill it with the values collected through your slicing.

* Group the DataFrame based upon the values within "IMDB User Votes Group".

* Find out how many rows fall into each group before finding the averages for "RottenTomatoes", "RottenTomatoes_User", "Metacritic", "Metacritic_User", and "IMDB".

## References

FiveThirtyEight (2015). [https://github.com/fivethirtyeight/data/tree/master/fandango](https://github.com/fivethirtyeight/data/tree/master/fandango)

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python

# Import Dependencies
import pandas as pd
# Create a path to the csv and read it into a Pandas DataFrame
csv_path = "Resources/movie_scores.csv"
movies_df = pd.read_csv(csv_path)

movies_df.head()

# Figure out the minimum and maximum IMDB user vote count
print(movies_df["IMDB_user_vote_count"].max())
print(movies_df["IMDB_user_vote_count"].min())

# Create bins in which to place values based upon IMDB vote count
bins = [0, 2499, 4999, 9999, 14999, 19999, 29999, 49999, 99999, 350000]

# Create labels for these bins
group_labels = ["0 to 2.4k", "2.5k to 4.9k", "5k to 9k", "10k to 14k", "15k to 19k", "20k to 29k",
                "30k to 49k", "50k to 99k", "100k to 350k"]
# Slice the data and place it into bins
pd.cut(movies_df["IMDB_user_vote_count"], bins, labels=group_labels).head()

# Place the data series into a new column inside of the DataFrame
movies_df["IMDB User Votes Group"] = pd.cut(movies_df["IMDB_user_vote_count"], bins, labels=group_labels)
movies_df.head()


# Create a GroupBy object based upon "IMDB User Votes Group"
imdb_group = movies_df.groupby("IMDB User Votes Group")

# Find how many rows fall into each bin
print(imdb_group["IMDB"].count())

# Get the average of each of the first 5 rating columns within the GroupBy object
imdb_group[["RottenTomatoes", "RottenTomatoes_User", "Metacritic", "Metacritic_User", "IMDB"]].mean()

```
{{% /expand%}}