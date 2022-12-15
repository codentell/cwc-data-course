+++
title = "11. Sentence Breaker 👩‍🎓👨‍🎓"
weight = 11
tags = ["vba"] 
+++



# Sentence Breaker

Now, it’s your turn to create a macro by using the `Split()` function that identifies the n-th word in a user-provided sentence. This is a challenging assignment, so take your time on it. Try to work through it piece by piece.

## Instructions

The starter workbook has a cell containing a written sentence and several cells with numbers to identify the n-th word of the sentence.

The starter code provided in `sentence_breaker.vbs` has comments to guide you.

1. Retrieve the user sentence and store it in a variable.

2. Retrieve the user word numbers and store them in variables.

3. Split the user sentence into separate words.

4. Use the word numbers to retrieve specific words in the sentence.

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub SentenceBreaker()

    ' Retrieve the user sentence and store in variable
    Dim Sentence As String
    Sentence = Cells(1, 2).Value
    MsgBox (Sentence)

    ' Retrieve the user word numbers and store in variables
    Dim num1 As Integer
    Dim num2 As Integer
    Dim num3 As Integer

    num1 = Cells(4, 1).Value
    num2 = Cells(5, 1).Value
    num3 = Cells(6, 1).Value

    MsgBox (num1)
    MsgBox (num2)
    MsgBox (num3)

    ' Split the user's sentence into words
    Dim SentenceArray() As String
    SentenceArray = Split(Sentence, " ")

    ' Use the word numbers to retrieve the specific words in the sentence
    ' Remember to offset by the 0 index
    Cells(4, 2).Value = SentenceArray(num1 - 1)
    Cells(5, 2).Value = SentenceArray(num2 - 1)
    Cells(6, 2).Value = SentenceArray(num3 - 1)
    

End Sub
```
{{% /expand%}}