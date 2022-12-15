+++
title = "01. Star Counter 👩‍🎓👨‍🎓"
weight = 1
tags = ["vba"] 
+++


# Star Counter

The dataset you'll be working with for this activity contains 50 rows of customer review data for French and Spanish online learning programs. Columns D through H contain the number of stars each program received as feedback. For example, the first row of the data indicates that a French program received two out of five stars in Monnie Mccasland's review.

Data stored this way can be difficult to analyze, so you'll be using VBA to convert it to numerical data.

## Instructions

Create a VBA script that tallies the number of "Full Stars" per row and enters them into the Total column. Starter code is provided, but feel free to start from scratch if you want an extra challenge.

## Bonus

Instead of hard-coding the final number of the loop, use VBA to determine the last row automatically (so, do not use `for i = 2 to 51`).

Create two charts:

* A bar chart to check if there is a relationship between program type and rating.

* A line graph to see if there is a relationship between date and rating.

## Hints

  * You will need to use a nested `for` loop.

  * You will need to create a variable to hold the number of stars and you will need to continually reset this variable at the start of each row.

—


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
' StarCounter
' 1. Create a nested for loop that iterates through each student.
' 2. For each loop count the number of instances of the word "Full-Star" using a counter
' 3. Save the counter value to the total cell
' 4. BONUS: Instead of hard-coding the last number of the loop, use VBA to determine the last row.
' 5. BONUS: Create two charts:
     ' One to see if there is a relationship between Program type and Rating
     ' One to see if there is a relationship between Date and Rating

Sub StarCounter()

  ' Create a variable to hold the StarCounter. We will repeatedly use this.
  dim StarCounter as Integer

  ' Loop through each row
  for i = 2 to 51

    ' Initially set the StarCounter to be 0 for each row
    StarCounter = 0

    ' While in each row, loop through each star column
    for j = 4 to 8

      ' If a column contains the word "Full-Star"...
      if (Cells(i, j).value = "Full-Star") then

        ' Add 1 to the StarCounter
        StarCounter = StarCounter + 1

      end if

    Next j

    ' Once we've iterated through each column in row i, print the value in the total column.
    Cells(i, 9).value = StarCounter

  Next i

End Sub
```

# Bonus 
```vb
' StarCounter
' 1. Create a nested for loop that iterates through each student.
' 2. For each loop count the number of instances of the word "Full-Star" using a counter
' 3. Save the counter value to the total cell
' 4. BONUS: Instead of hard-coding the last number of the loop, use VBA to determine the last row.
' 5. BONUS: Create two charts:
     ' One to see if there is a relationship between Program type and Rating
     ' One to see if there is a relationship between Date and Rating

Sub StarCounter()

  ' Create a variable to hold the StarCounter. We will repeatedly use this.
  Dim StarCounter As Integer
  
  ' BONUS: counts the number of rows
  lastrow = Cells(Rows.Count, 1).End(xlUp).Row
 
  ' Loop through each row
  ' BONUS: use lastrow variable instead of 51
  For i = 2 To lastrow

    ' Initially set the StarCounter to be 0 for each row
    StarCounter = 0

    ' While in each row, loop through each star column
    For j = 4 To 8

      ' If a column contains the word "Full-Star"...
      If (Cells(i, j).Value = "Full-Star") Then

        ' Add 1 to the StarCounter
        StarCounter = StarCounter + 1

      End If

    Next j

    ' Once we've iterated through each column in row i, print the value in the total column.
    Cells(i, 9).Value = StarCounter

  Next i
  

End Sub
```
{{% /expand%}}
