+++
title = "03. Gradebook 👩‍🎓👨‍🎓"
weight = 3
tags = ["vba"] 
+++


# VBA Grade Book

In this activity, you will create a macro that will check a student’s numerical grade, assign them a letter grade, and apply different formatting changes to a cell depending on the value of the student’s grade.

## Instructions

With `grader.xlsm` as your starting point, create a grade calculator using **conditionals**. This calculator will convert a student's numeric grade into a letter grade and then style the resulting cell accordingly.

Once complete, your script should perform the following:

* If the score is 90 or higher:
  * Add an "A" in the letter grade cell.
  * Fill the Pass/Warning/Fail cell with the color green.
  * Add the text “Pass” to the Pass/Warning/Fail cell.

* If the score is greater than or equal to 80 and less than 90:
  * Add a "B" in the letter grade cell.
  * Fill the Pass/Warning/Fail cell with the color green.
  * Add the text “Pass” to the Pass/Warning/Fail cell.


* If the score is greater than or equal to 70 and less than 80:
  * Add a "C" in the letter grade cell.
  * Fill the Pass/Warning/Fail cell with the color yellow.
  * Add the text "Warning" to the Pass/Warning/Fail cell.

* Finally, if the score is below 70:
  * Add an “F” in the letter grade cell.
  * Fill the Pass/Warning/Fail cell with the color red.
  * Add the text “Fail” to the Pass/Warning/Fail cell.

## Bonus

Create a second button that resets the grades to the original state and then establishes the previous grade in a row labeled "Last Grade."

—


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub GradeBook()

  ' Check if the student's grade is greater than or equal to 90...
  If Cells(2, 2).Value >= 90 Then

      ' Establish that the grade is Passing
      Cells(2, 3).Value = "Pass"

      ' Color the Passing grade green
      Cells(2, 3).Interior.ColorIndex = 4

      ' Set the letter grade to "A"
      Cells(2, 4).Value = "A"

  ' Check if the student's grade is greater than or equal to 80...
  ElseIf Cells(2, 2).Value >= 80 Then

      ' Establish that the grade is Passing
      Cells(2, 3).Value = "Pass"

      ' Color the Passing grade green
      Cells(2, 3).Interior.ColorIndex = 4

      ' Set the letter grade to "B"
      Cells(2, 4).Value = "B"

  ' Check if the student's grade is greater than or equal to 70...
  ElseIf Cells(2, 2).Value >= 70 Then

      ' Establish that the grade is a Warning
      Cells(2, 3).Value = "Warning"

      ' Color the Warning grade yellow
      Cells(2, 3).Interior.ColorIndex = 6

      ' Set the letter grade to "C"
      Cells(2, 4).Value = "C"

  ' Check if the students' grade is failing
  Else

      ' Establish that the grade is Failing
       Cells(2, 3).Value = "Fail"

      ' Color the Failing grade red
      Cells(2, 3).Interior.ColorIndex = 3

      ' Set the letter grade to "F"
      Cells(2, 4).Value = "F"

  End If

End Sub
```

# reset button

````vb
Sub Reset_Button():

  ' Pass the previous grade to the Last Grade row
  Cells(12, 2).Value = Cells(2, 2).Value
  Cells(12, 3).Value = Cells(2, 3).Value
  Cells(12, 4).Value = Cells(2, 4).Value

  ' Empty out the current grade and remember to set the color back to default
  Cells(2, 2).Value = ""
  Cells(2, 3).Value = ""
  Cells(2, 3).Interior.ColorIndex = 0
  Cells(2, 4).Value = ""

End Sub


```
{{% /expand%}}
