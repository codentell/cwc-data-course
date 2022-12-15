+++
title = "10. Splitting 👩‍🏫🧑‍🏫"
weight = 10
tags = ["vba"] 
+++

```vb
Sub SimpleArrays():
    
    ' String Splitting Example
    ' ------------------------------------------
    Dim Words() As String
    Dim Shakespeare As String
    Shakespeare = "To be or not to be. That is the question"

    ' Break apart the Shakespeare quote into individual words
    Words = Split(Shakespeare, " ")

    ' Print individual word
    MsgBox (Words(5))

End Sub


```