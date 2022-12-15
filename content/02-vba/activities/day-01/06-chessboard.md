+++
title = "06. Chessboard  👩‍🎓👨‍🎓"
weight = 6
tags = ["vba"] 
+++

# Chessboard

![Images/06-ChessBoard_1.png](../images/06-ChessBoard_1.png)


For this activity, you'll add the names of chess pieces to their starting positions on the provided chessboard.

## Instructions

* Add text-based chess pieces to the provided chessboard. For the first two rows of the chessboard, use `Ranges`; for the final two rows of the chessboard, use `Cells`.

Piece positions:

| Rook | Knight | Bishop | Queen | King | Bishop | Knight | Rook |
|----|----|----|----|----|----|----|----|
| Pawn | Pawn | Pawn | Pawn | Pawn | Pawn | Pawn | Pawn |
| &nbsp; |  |  |  |  |  |  |  |
| &nbsp; |  |  |  |  |  |  |  |
| &nbsp; |  |  |  |  |  |  |  |
| &nbsp; |  |  |  |  |  |  |  |
| Pawn | Pawn | Pawn | Pawn | Pawn | Pawn | Pawn | Pawn |
| Rook | Knight | Bishop | Queen | King | Bishop | Knight | Rook |

## Hint

Remember that with `Ranges`, it is possible to modify multiple cells at once.

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub ChessBoard()

  ' Using Ranges
  ' ---------------------------------------

  ' Insert Pawns
  Range("A2:H2").value = "Pawn"

  ' Insert Rooks
  Range("A1, H1").value = "Rook"

  ' Insert Knights
  Range("B1, G1").value = "Knight"

  ' Insert Bishops
  Range("C1, F1").value = "Bishop"

  ' Insert Queen
  Range("D1").value = "Queen"

  ' Insert King
  Range("E1").value = "King"

  ' Using Cells
  ' ---------------------------------------

  ' Insert Pawns
  Cells(7, 1).value = "Pawn"
  Cells(7, 2).value = "Pawn"
  Cells(7, 3).value = "Pawn"
  Cells(7, 4).value = "Pawn"
  Cells(7, 5).value = "Pawn"
  Cells(7, 6).value = "Pawn"
  Cells(7, 7).value = "Pawn"
  Cells(7, 8).value = "Pawn"

  ' Insert Rooks
  Cells(8, 1).value = "Rook"
  Cells(8, 8).value = "Rook"

  ' Insert Knights
  Cells(8, 2).value = "Knight"
  Cells(8, 7).value = "Knight"

  ' Insert Bishops
  Cells(8, 3).value = "Bishop"
  Cells(8, 6).value = "Bishop"

  ' Insert Queen
  Cells(8, 4).value = "Queen"

  ' Insert King
  Cells(8, 5).value = "King"

End Sub
```


{{% /expand%}}