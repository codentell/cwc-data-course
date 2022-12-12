+++
title = "10. Top Songs Pivot 👩‍🎓👨‍🎓"
weight = 10
tags = ["excel"] 
+++

# Top-Songs Pivot Table

Solution you will be working toward is in the following image:

![](../images/08-TopPivot.png)

Pivot tables are exceptionally helpful when dealing with large-scale datasets that contain similarities between data points. For this activity, you will take a 5000-row spreadsheet containing data on the top-5000 songs from 1901 to today, and you’ll use pivot tables to figure out the artists with the most songs in the top 5000, what those songs are, and what year they came out.

## Instructions

* Select all of the data within your worksheet, and then create a new pivot table.

* Make a pivot table that can be filtered by 'year' and contains two rows: 'artist' and 'name'.

  * All of an artist's songs should be listed underneath their name.

* Update your pivot table to contain values for:

  * How many songs an artist has in the top 5000.
  * The sum of the final_score of their songs.

* Sort your pivot table by descending sum of the final_score.

## References

* The World's Music Charts "All Time Songs" T Sort, Hawtin, S. et al, version 2.8.0044 [https://tsort.info/csv/top5000songs-2-8-0044.csv](https://tsort.info/csv/top5000songs-2-8-0044.csv) from [https://tsort.info/music/songs0.htm](https://tsort.info/music/songs0.htm)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}

* The "Rows" for the pivot table have Artist as the main category and Song Name as the subcategory, so all songs are stored under their artist's name.

* To determine how many songs an artist has in the original chart, place "artist" into the "Values" section, then count how many times their name appears. The sum of "final_score" is self-explanatory.

* To sort the chart based on an artist's overall score, click on the "Sum of Final_Score" column within the pivot table and select "Sort From Largest to Smallest."

* The following image captures the key points for this discussion:

![Top Song 5000](../images/Top5000SongsPivot.png)

{{% /expand%}}
