+++
title = "03. Button Clicks 👩‍🏫🧑‍🏫"
weight = 3
tags = ["vba"] 
+++


* **Files**: **03-Ins_ButtonClicks**

* Next, return to the **Developer tab**, where you’ll  insert a button in their spreadsheet. The Mac layout is slightly different, so be patient if you have any difficulty finding features across operating systems.

* First, create a button, as in the following image:
![Images/03-ButtonClicks_2.png](../images/03-ButtonClicks_2.png)

* Once the button is created, the "Assign Macro" window will pop up, where you can choose to create a new macro or select an existing one, as in the following image:
![Images/03-ButtonClicks_3.png](../images/03-ButtonClicks_3.png)

* If you accidentally close this window, you can always re-open it by right-clicking your button and selecting "Assign Macro"

* If using the Excel file provided in 03-Ins_ButtonClicks, the button will be associated with a macro that simply prints "You clicked me" when the button is pressed, as in the following image:
![Images/03-ButtonClicks_4.png](../images/03-ButtonClicks_4.png)



```vb
Sub Button3_Click()
    MsgBox ("You clicked me!")
End Sub
```

