+++
title = "06. Credit Card Checker 👩‍🎓👨‍🎓"
weight = 6
tags = ["vba"] 
+++

# Credit Card Checker

In this activity, you will practice comparing cells to calculate the total transaction amount for different credit card brands.

## Instructions

* Create a VBA script that will process the credit card purchases by identifying each of the unique brands listed.

* Create a single pop-up message for each of the credit card brands listed by looping through the list.

## Bonus

Add up the total value of credit card purchases for each brand, and put the information in the summary table.


## Note

* This assignment is extremely similar to the basic version of the homework assignment, so let's buckle down and analyze our work!

—


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub credit_card()

  ' Set an initial variable for holding the brand name
  Dim Brand_Name As String

  ' Loop through all credit card purchases
  For i = 2 To 101

    ' Check if we are still within the same credit card brand, if we are not...
    If Cells(i + 1, 1).Value <> Cells(i, 1).Value Then

      ' Message Box the unique Bank Name
      MsgBox(Cells(i, 1).Value)

    End If

  Next i

End Sub
```

# Bonus

```vb
Sub credit_card()

  ' Set an initial variable for holding the brand name
  Dim Brand_Name As String

  ' Set an initial variable for holding the total per credit card brand
  Dim Brand_Total As Double
  Brand_Total = 0

  ' Keep track of the location for each credit card brand in the summary table
  Dim Summary_Table_Row As Integer
  Summary_Table_Row = 2

  ' Loop through all credit card purchases
  For i = 2 To 101

    ' Check if we are still within the same credit card brand, if it is not...
    If Cells(i + 1, 1).Value <> Cells(i, 1).Value Then

      ' Set the Brand name
      Brand_Name = Cells(i, 1).Value

      ' Add to the Brand Total
      Brand_Total = Brand_Total + Cells(i, 3).Value

      ' Print the Credit Card Brand in the Summary Table
      Range("G" & Summary_Table_Row).Value = Brand_Name

      ' Print the Brand Amount to the Summary Table
      Range("H" & Summary_Table_Row).Value = Brand_Total

      ' Add one to the summary table row
      Summary_Table_Row = Summary_Table_Row + 1
      
      ' Reset the Brand Total
      Brand_Total = 0

    ' If the cell immediately following a row is the same brand...
    Else

      ' Add to the Brand Total
      Brand_Total = Brand_Total + Cells(i, 3).Value

    End If

  Next i

End Sub
```
{{% /expand%}}
