+++
title = "05. Fizz Buzz 👩‍🎓👨‍🎓"
weight = 5
tags = ["vba"] 
+++

# Fizz Buzz

In this activity, you'll work on a popular logic problem that countless coders have encountered in technical interviews.

## Instructions

Create a VBA script that populates the second column with the word "Fizz", "Buzz", or "Fizzbuzz" based on the value in the first column.

* If the value in Column 1 is a multiple of both 3 and 5, print "Fizzbuzz" in Column 2.

* If the value in Column 1 is a multiple of just 3, print "Fizz" in Column 2.

* If the value in Column 1 is a multiple of just 5, print "Buzz" in Column 2.

## Hint

Remember the mod!

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub FizzBuzz()
    ' Loop through the values in Column 1
    For i = 2 To 100

        'Set cell value to variable
        num = Cells(i, 1).Value


        ' Check if the number is divisible by 3 and 5....
        If (num Mod 3 = 0 And num Mod 5 = 0) Then

            ' If so, print Fizzbuzz
            Cells(i, 2).Value = "Fizzbuzz"

        ' Check if the number is divisible by just 3...
        ElseIf (num Mod 3 = 0) Then

            ' If so, print "Fizz"
            Cells(i, 2).Value = "Fizz"

        ' Check if the number is divisible by just 5...
        ElseIf (num Mod 5 = 0) Then

            ' If so, print "Buzz"
            Cells(i, 2).Value = "Buzz"

        End If

    Next i

End Sub
```
{{% /expand%}}