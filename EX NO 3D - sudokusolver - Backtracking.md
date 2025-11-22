
# EX 3D Sudoku solver - Backtracking.
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Start and read the 9×9 Sudoku grid, where empty cells are represented by 0.
2. For each empty cell, try placing digits from 1 to 9, checking with isSafe() that the number doesn’t already exist in the current row, column, or 3×3 subgrid.
3. If a valid number is found, place it and recursively move to the next cell; if no valid number fits, backtrack by resetting the cell to 0.
4. Continue the recursive process until all cells are filled correctly, indicating a solved Sudoku.
5. Print the completed Sudoku board if solvable; otherwise, display that no valid solution exists and stop.

## Program:
#### Developed by: ARCHANA T
#### Register Number: 212223240013 
```
import java.util.Scanner;

public class SudokuSolver {

    // Check if it's safe to place the number
    static boolean isSafe(int[][] board, int row, int col, int num) {
        // Check row and column
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        // Check 3x3 subgrid
        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    // Recursive backtracking solver
    static boolean solveSudoku(int[][] board, int row, int col) {
        //Type your code here
        if(row==8 && col==9){
            return true;
        }
        if(col==9){
            row++;
            col=0;
        }
        if(board[row][col]!=0){
            return solveSudoku(board,row,col+1);
        }
        for(int num=1;num<=9;num++)
        {
            if(isSafe(board,row,col,num))
            {
                board[row][col]=num;
                
                if(solveSudoku(board,row,col+1))
                {
                    return true;
                }
                board[row][col]=0;
            }
        }
        return false;
    }
    
    

    // Utility to print the board
    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      //  System.out.println("Enter the Sudoku puzzle row by row (use 0 for empty cells):");

        for (int i = 0; i < 9; i++) {
            //System.out.print("Enter row " + (i + 1) + ": ");
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

      //  System.out.println("\nSolving...\n");

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}


```

## Output:
<img width="716" height="579" alt="image" src="https://github.com/user-attachments/assets/c3f3ea03-9605-44d5-a5fb-b00986fe563b" />



## Result:
The program successfully implemented and the expected output is verified.
