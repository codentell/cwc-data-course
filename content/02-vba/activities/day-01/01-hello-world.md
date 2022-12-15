+++
title = "01. Hello World👩‍🏫🧑‍🏫"
weight = 1
tags = ["vba"] 
+++


* **Files:** Activities/01-Ins_HelloWorld/Solved/hello_world.xlsm

* The first VBA script. Open the VBA editor, and navigate to Module 1. All examples in this lesson plan and the ones in the rest of the unit can be found in Module 1, as in the following images:

  ![Images/developer.png](../images/developer.png)

  ![Images/module1.png](../images/module1.png)

* The editor’s interface, and be sure to discuss the following points:

  * Modules are organizational units of VBA code that are usually attached to a workbook or worksheet. We can create modules by right-clicking on a workbook or worksheet and then selecting "Insert Module."

  * Once inside a module, we can start writing a VBA script. In our case, we've already created a script that will trigger Excel to deliver a pop-up message.

* VBA will run subroutines based on where the cursor is. Make sure your cursor is inside the `HelloWorld` subroutine, then the play button in your VBA editor to trigger the “Hello World” pop-up message box, as in the following images.

  ![Images/01-HelloWorld_2.png](../images/01-HelloWorld_2.png)

  ![Images/01-HelloWorld_3.png](../images/01-HelloWorld_3.png)

  * The code begins with the keyword `Sub`, which is short for subroutine. This line is followed by `HelloWorld()`, which marks the title of our subroutine. The empty brackets indicate that our subroutine takes in no arguments. Explain that we'll cover functions, which _do_ take in arguments, at a later point.

  * Then, explain that our subroutine has one objective&mdash;to create a pop-up message box (`MsgBox`) containing the phrase "Hello World".

  * Finally, explain that once our subroutine has triggered our pop-up message, its work is done, and the subroutine is complete, which is denoted by the `End Sub` keywords. Emphasize that every subroutine must begin with the keyword `Sub` and end with `End Sub`.

# Code
```vb
Sub HelloWorld():
  MsgBox("Hello World")
End Sub
```