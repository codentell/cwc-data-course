+++
title = "08. Calculator 👩‍🎓👨‍🎓"
weight = 8
tags = ["vba"] 
+++

# Calculator

Now, you will have the opportunity to use data in a spreadsheet to create variables and perform a simple calculation.

## Instructions

* Using the spreadsheet and unsolved VBS code as a starter, complete the script so that `Price`, `Tax`, `Quantity`, and `Total` are stored in variables.

* Then, assign these variables the value of their associated cell in the spreadsheet.

* Once complete, your code should set the `Total` value in the spreadsheet.

* Create a pop-up message that states the total value: "Your total is $45.00."

## Bonus

Try to complete the exercise _without_ looking at the starter code.

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub VariableSetting():

    ' Create variables for the Price, Tax, Quantity, and Total
    Dim Price As Double
    Dim Tax As Double
    Dim Quantity As Double
    Dim Total As Double

    ' Retrieve and store the data values in each variable
    Price = Range("B2").Value
    Tax = Range("C2").Value
    Quantity = Range("D2").Value

    ' Calculate the total by using each of the variables
    Total = Price * (1 + Tax) * Quantity

    ' Create a Message Box for the Total and insert into cell
    MsgBox ("Your total is $" + Str(Total))
    Range("E2").Value = Total

End Sub
```

{{% /expand%}}
