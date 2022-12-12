+++
title = "11. Lookups 👩‍🏫🧑‍🏫"
weight = 11
tags = ["excel"] 
+++

* VLOOKUP() takes in four values: a lookup value, the range of a table, the index number for a column within that range, and the match parameter.

* VLOOKUP() searches for a value, it is only looking for matches within the leftmost column of the range that they have selected.

Since the formula listed specifies 3 as the column index, it will grab the value stored within the third column of the second table. As such, it is grabbing the value stored within the "Role" column, as captured in the following image:

![](../images/09-VLookups_1.png)

The match parameter indicates either an exact match (FALSE) or an approximate match (TRUE).

* HLOOKUP() is almost identical to VLOOKUP(), except it searches through ranges horizontally instead of vertically. Therefore, this formula searches through rows instead of columns.

