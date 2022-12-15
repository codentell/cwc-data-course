+++
title = "04. Checkerboard layout 👩‍🎓👨‍🎓"
weight = 4
tags = ["vba"] 
+++

# Checkerboard Layout

In this activity, you will work with a partner to create a checkerboard.

## Instructions

Using VBA scripts, create an 8-by-8 grid with alternating red and black squares.

## Hints

* You will need to use nested `for` loops, conditionals, the `MOD` function, and formatting to create the board.

* This is a tricky problem! Try to pseudocode a plan first.

* Unlike previous activities, this one can be solved in many different ways. While some methods may be more efficient, simply finding a solution to the problem is a great start!

—


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
# checkboard
```vb
Sub CheckerBoard()

  ' Setup a counter to track cell number
  Dim cellnumber as Integer
  Dim i, j As Integer
  cellnumber = 1

  ' Loop through each row of the board
  For i = 1 to 8

    ' Loop through each column of the board
    For j = 1 to 8

      ' If we are on a cell that is divisible by 2 then color it black
      If (cellnumber Mod 2 = 0) then

        Cells(i, j).Interior.ColorIndex = 1

      ' Otherwise color it red
      Else

        Cells(i, j).Interior.ColorIndex = 3

      End if

      ' Add one to our cell number each time
      cellnumber = cellnumber + 1

    Next j

    ' Whenever we start on a new row, we also add one to the cell number (to create the alternation)
    cellnumber = cellnumber + 1

  Next i

End Sub
```

# conditional loops 

```vb
Sub conditional_loops()

    ' Create a for loop from 1 to 10
    For i = 1 To 10
        Cells(i, 1).Value = i

        ' Use the modulus function to determine if a number is divisible by 2 (even number)
        If Cells(i, 1).Value Mod 2 = 0 Then

            ' Enter "Even Row" the adjacent cell
            Cells(i, 2).Value = "Even Row"
            
        ' If the number is not divisible by 2 (odd number)
        Else

            ' Enter "Even Row" the adjacent cell
            Cells(i, 2).Value = "Odd Row"
            
        ' Close the If/Else Statement
        End If

    Next i

End Sub
```
{{% /expand%}}
