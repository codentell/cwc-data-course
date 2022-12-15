+++
title = "04.  Loop Conditional 👩‍🏫🧑‍🏫"
weight = 4
tags = ["vba"] 
+++

# conditional 
```vb
Sub conditional_loops()

    ' Create a for loop from 1 to 10
    For i = 1 To 10

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

# mods

```vb
Sub modulo()

    ' Remainder of 0
    Cells(2, 1).Value = 4 Mod 2
    
    ' Remainder of 1
    Cells(3, 1).Value = 5 Mod 4
    
    ' Remainder of 3
    Cells(4, 1).Value = 11 Mod 8
    
    ' Remainder of 2
    Cells(5, 1).Value = 23 Mod 7
    
    ' Remainder of 5
    Cells(6, 1).Value = 24 Mod 19

End Sub
```