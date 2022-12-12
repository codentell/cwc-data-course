+++
title = "07. Formatting 👩‍🏫🧑‍🏫"
weight = 7
tags = ["excel"] 
+++

### NumberType 
File: 
* **07-Ins_Formatting/NumberTypes.xlsx**

* Excel can style the numeric data of a spreadsheet so that it looks a certain way. This can be done by selecting a cell or a range of numeric data, clicking on the "Number" group, and then selecting any of the available numeric styles.

* It is important to note that we are only altering the look or appearance of the number. In the following image, the data itself is the same as it was before we applied the styling, but we’ve formatted the original value as a currency:


 ![Number Formats](../images/NumberFormats.png)

 ---

 ### Conditional Formatting
File: 
* **07-Ins_Formatting/ConditionalFormatting.xlsx**

* We can make in-depth formatting changes to a spreadsheet by altering the styling of the cells on the page. 

  * Each cell within the "Favorite Color" column is being painted a certain color based on the value contained in the cell.

  * The cells in the C2 to H2 range are being painted based on how many times each color appears in the "Favorite Color" column.

  * This kind of formatting could be applied manually, but it would be tedious and need to be redone any time the data changed. Thankfully, Excel includes the option to format cells based on conditionals.

  * Click on the "Conditional Formatting" option within Excel's "Home" tab and select "Manage Rules" from the menu that appears. Now, you can examine the formatting rules for the entire worksheet.

  * **Conditional Formatting** changes the styling of a cell based on certain conditions. As such, this sheet includes rules that style cells based on the values that the cells contain, as captured in the following GIF:

  ![images/06-Formatting.png](../images/06-Formatting.png)