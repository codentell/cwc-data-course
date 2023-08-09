+++
title = "08. Cypto Kennel 👩‍🎓👨‍🎓"
weight = 8
tags = ["vba"] 
+++

# Crypto Kennel

The spreadsheet you'll be working with in this activity is full of animal inspired cryptocurrency! In place of numerical data, when you open your file you'll be greeted by cells filled with the words "Shiba Inu", "Dogecoin", or "Cat Token", however your crypto kennel is for canines only! Instead of manually removing the unwanted feline crypto, you'll use VBA to do the work for you.

## Instructions

* Create a VBA script to handle the over-abundance of the `Cat Token` currency in your spreadhseet's "crypto kennel".

* There are three parts to this problem:

  * **Part 1:** Count the number of times `Cat Token` appears and display the number to your user in the form of a message box.

  * **Part 2:** Modify the script such that it changes the word `Cat Token` to `Dogecoin`.

  * **Part 3:** Modify the script a third time, this time keeping in mind that you have a limited number of `Shiba Inu` and `Dogecoin`. Use the full set of `Shiba Inu` and `Dogecoin` you have available to replace all instances of `Cat Token`. If you run out of `Shiba Inu` or `Dogecoin` provide the user with the message: "Oh no! We still have some Cat Token..."

## Hints

* You may want to create a backup of your spreadsheet as your macro will write over the contents.

* Take lots of deep breaths!

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
' Part 1: Count the number of times Cat Token appears
' Part 2: Each time you find a Cat Token replace it with Dogecoin
' Part 3: You have a max amount of Shiba Inu and Dogecoin, utilize no more than what's provided.
'           If there are still instances of Cat Token left, provide the user with a message stating: "Oh no! We still have some Cat Token..."

Sub CryptoKennel()

  ' PART 3
  ' ------------------------------------------------
  ' Create a variable to hold the number of Cat Token
  Dim CatCount As Integer

  ' Create a variable to hold the number of Shiba Inu and Dogecoin
  Dim ShibaCount As Integer
  Dim DogeCount As Integer

  ' Set the value of Shiba Inu and Dogecoin counters
  ShibaCount = Range("I2").Value
  DogeCount = Range("I5").Value

  ' Set the initial value for the CatCount to 0
  CatCount = 0

  ' Loop through all rows
  For i = 1 To 6

    ' Loop through all columns
    For j = 1 To 7

      ' If the value of a cell is equal to Cat Token
      If Cells(i, j).Value = "Cat Token" Then

        ' Add to the CatCounter
        CatCount = CatCount + 1

        ' Check if we have Shiba Inu available
        If (ShibaCount > 0) Then

          ' Replace the Cat Token with Shiba Inu
          Cells(i, j).Value = "Shiba Inu"

          ' Subtract from the Shiba Inu Count
          ShibaCount = ShibaCount - 1

        ' Check if we have Dogecoin available
        ElseIf (DogeCount > 0) Then

          ' Replace the Cat Token with Dogecoin
          Cells(i, j).Value = "Dogecoin"

          ' Subtract from the Dogecoin Count
          DogeCount = DogeCount - 1

        End If

      End If

    Next j

  Next i

  ' Show the number of Cat Token found
  MsgBox (CatCount & " Cat Token Found")

  ' Create the final message if we still have Cat Token
  If (Range("I2").Value + Range("I5").Value < CatCount) Then

    MsgBox ("Oh no! We still have some Cat Token... ")

  End If

End Sub
```
{{% /expand%}}