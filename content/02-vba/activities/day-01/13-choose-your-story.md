+++
title = "13. Choose your story  👩‍🎓👨‍🎓"
weight = 11
tags = ["vba"] 
+++

# Choose Your Story

In this activity, you will practice using conditionals by creating the first step of a role-playing adventure.

## Instructions

Create an Excel workbook and VBA macro that provides a user with an input field and a single button. Based on the user-input number (1, 2, 3, or 4), the button will trigger different message boxes as follows:

* If the user enters a value of 1, display “You choose to enter the wooded forest of doom!”

* If the user enters a value of 2, display “You choose to enter the fiery volcano of doom!”

* If the user enters a value of 3, display “You choose to enter the terrifying jungle of doom!”

*  If the user enters a value of 4, display a similar custom message.

* If the user enters anything else, display “You decide to stay home instead.”

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub Begin_Journey()
    
    ' Use conditionals to change message box based on user input
    If (Range("B1").Value = 1) Then
        MsgBox ("You choose to enter the wooded forest of doom!")

    ElseIf (Range("B1").Value = 2) Then
        MsgBox ("You choose to enter the fiery volcano of doom!")

    ElseIf (Range("B1").Value = 3) Then
        MsgBox ("You choose to enter the terrifying jungle of doom!")

   ElseIf (Range("B1").Value = 4) Then
        MsgBox ("You choose to enter the bathroom")

    Else
        MsgBox ("You decide to stay home instead.")

    End If
End Sub


```
{{% /expand%}}