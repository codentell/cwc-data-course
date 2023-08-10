+++
title = "01. Warmup 👩‍🎓👨‍🎓"
weight = 1
tags = ["vba"] 
+++

# Budget Checker

In this activity, you'll write a VBA script to run a budget checker in Excel.

## Instructions

* There are three parts to this problem.

  * Part 1: Calculate the total amount after adding in the fee, and enter the value in the "Total" cell.

  * Part 2: Create a message box to alert the user if the total amount, including the fee, is within or over budget.

  * Part 3 (Challenge): If the total is over budget, correct the price so it fits within the user’s budget. Be sure to round down!

    * For example: If the user's budget is 100 and the fees are 15%, the max price should be 86.

## Hints

* Break up the problem into smaller steps.

* Look at old code! You got this!

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
' Part I: Calculate the total after fees
' Part II: Create an alert if the item is above budget after fees.
' Part III: If the item is above budget, correct the price such that it would be "under budget"

' ----------------------------------------------------

Sub BudgetChecker()

    ' Part I
    ' ----------------------------------------------------

    ' 1. Retrieve the Price and Fees from the cells
    Dim total As Double

    ' 2. Use these values to calculate the total
    total = Range("F3").Value * (1 + Range("H3").Value)
    ' msgbox(total)

    ' 3. Enter the total into the appropriate cell
    Range("L3").Value = total

    ' Part II
    ' ----------------------------------------------------
    ' 4. Create a variable to store budget
    Dim budget As Double
    budget = Range("B3").Value
    ' MsgBox(budget)

    ' 5. Compare using conditionals whether total is greater than or less than the budget
    If budget > total Then

        MsgBox ("Under budget")

    Else

        MsgBox ("Over budget")

        ' Part III
        ' ----------------------------------------------------
        Dim newPrice As Double
        newPrice = budget / (1 + Range("H3").Value)

        'Use a worksheet function to round the new price down to the nearest whole dollar
        newPrice = Application.WorksheetFunction.RoundDown(newPrice, 0)

        ' Change the price
        Range("F3").Value = newPrice

        ' Change the new total
        Range("L3").Value = newPrice * (1 + Range("H3").Value)

    End If


```
{{% /expand%}}