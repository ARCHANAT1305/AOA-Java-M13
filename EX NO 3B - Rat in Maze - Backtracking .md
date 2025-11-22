# EX 3B Rat in Maze- Backtracking 
## AIM:
To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm
1. Start and read the maze dimensions, the maze matrix, the start position, and the destination position
2. Initialize a visited matrix to track explored cells and define four possible movement directions (up, down, left, right).
3. From the start cell, use Depth-First Search (DFS) to explore paths — moving continuously in one direction until hitting a wall or maze boundary.
4. After hitting a wall, step back to the last valid position and recursively continue the search from there if it hasn’t been visited.
5. If the destination is reached, return true; if all possible paths are explored without reaching it, return false and stop.  

## Program:
#### Developed by: ARCHANA T
#### Register Number: 212223240013
```
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read maze dimensions
        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        // Read start position
        int[] start = new int[]{sc.nextInt(), sc.nextInt()};

        // Read destination position
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        if (visit[curr[0]][curr[1]]) {
            return false;
        }
        if (curr[0] == destination[0] && curr[1] == destination[1]) {
            return true;
        }

        visit[curr[0]][curr[1]] = true;
        int[] dirX = {0, 1, 0, -1};
        int[] dirY = {-1, 0, 1, 0};

        for (int i = 0; i < 4; i++) {
            int r = curr[0], c = curr[1];
            // Move in current direction until hitting wall or boundary
            while (r >= 0 && r < m && c >= 0 && c < n && maze[r][c] == 0) {
                r += dirX[i];
                c += dirY[i];
            }
            // Step back to last valid position
            r -= dirX[i];
            c -= dirY[i];
            if (dfs(m, n, maze, new int[]{r, c}, destination, visit)) {
                return true;
            }
        }
        return false;
    }

    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        boolean[][] visit = new boolean[m][n];
        return dfs(m, n, maze, start, destination, visit);
    }
}
```

## Output:

<img width="304" height="388" alt="image" src="https://github.com/user-attachments/assets/30cdbc8a-61b0-44a3-84ca-c239a61791f2" />


## Result:
The program successfully implemented and the expected output is verified.
