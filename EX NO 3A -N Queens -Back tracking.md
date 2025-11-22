
# EX 3A N Queens Problem - Backtracking Approach.
## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm
1. Start and read the board size N, then initialize an N × N chessboard with all zeros.
2. Place a queen in each column one by one, checking for a safe position in the current column.
3. Use the isSafe() function to ensure no other queen attacks the current position (checking row, upper diagonal, and lower diagonal on the left side).
4. If a safe position is found, place the queen and recursively attempt to place queens in the next column; if no safe position exists, backtrack.
5. Once all queens are placed successfully, print the board; otherwise, display that no solution exists, then stop   

## Program:
#### Developed By: ARCHANA T
#### REGISTER NUMBER :212223240013
```
import java.util.Scanner;

public class NQueens {
    static int N;

    // Function to print the solution
    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    // Function to check if a queen can be placed on board[row][col]
    static boolean isSafe(int[][] board, int row, int col) {
        // Check left side of current row
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

        // Check upper diagonal on left side
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        // Check lower diagonal on left side
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    // Recursive utility function to solve N-Queens
    static boolean solveNQUtil(int[][] board, int col) {
        if (col >= N)
            return true;

        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {
                board[i][col] = 1;

                if (solveNQUtil(board, col + 1))
                    return true;

                board[i][col] = 0; // Backtrack
            }
        }

        return false;
    }

    // Main solver function
    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

    // Driver method
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt(); // Accept board size
        solveNQ();
    }
}

```

## Output:
<img width="451" height="207" alt="image" src="https://github.com/user-attachments/assets/51717f5d-1a7a-4888-a030-aae38ea6f385" />



## Result:
The program successfully implemented and the ouput is verified. 
