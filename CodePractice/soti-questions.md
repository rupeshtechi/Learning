## SET-1:
1. To find the given string palindrome or not
2. The second is string permutations 
3. The third is on the graph 
4. The question there are two strings you have to find whether one string is a substring of another string or not. Here is the gfg problem

## Set–2:
1. A question regarding a maze where you could only move based on the specified numbers in the box you were in.
2. A question about a clock where you needed to convert an angle to all the times where the minute hand and the hour hand specified those times.
3. 1 squirrel eats 1 nut in 1 hour. In what time will 5 squirrels eat 9 nuts?

## Set–3:
1. OA game of life / last person to catch the bus
2. LC medium coin change
3. DS/algo – finding matching of content among similar file name and different content
4. Math – 1.5 people take 1.5 minutes to perform 1.5 tasks; how much task can be done by 9 people in 9 minutes?


## Set–4:
1. Three jars with known capacity, two filled, one empty — how to get an exact amount of liquid.
2. About DP queue — draw a pattern.
3. Check if 2 words are anagram?

```
using System;
using System.Collections.Generic;

class Program
{
    static int[] dr = { -1, 0, 1, 0 };  // Up, Right, Down, Left
    static int[] dc = { 0, 1, 0, -1 };

    class State
    {
        public int r, c, dir;
        public State(int r, int c, int dir)
        {
            this.r = r; this.c = c; this.dir = dir;
        }
    }

    static bool CanReach(int[,] maze, int sr, int sc, int tr, int tc)
    {
        int n = maze.GetLength(0);
        int m = maze.GetLength(1);

        bool[,,] visited = new bool[n, m, 4];
        Queue<State> q = new Queue<State>();

        // Truck initially facing "Right"
        q.Enqueue(new State(sr, sc, 1));
        visited[sr, sc, 1] = true;

        while (q.Count > 0)
        {
            var cur = q.Dequeue();

            if (cur.r == tr && cur.c == tc)
                return true;

            // 3 possible moves: forward, left+forward, right+forward

            for (int turn = -1; turn <= 1; turn++)
            {
                int newDir = (cur.dir + turn + 4) % 4;

                int nr = cur.r + dr[newDir];
                int nc = cur.c + dc[newDir];

                // Bounds
                if (nr < 0 || nc < 0 || nr >= n || nc >= m) 
                    continue;

                // Road must be open
                if (maze[nr, nc] == 1) 
                    continue;

                if (!visited[nr, nc, newDir])
                {
                    visited[nr, nc, newDir] = true;
                    q.Enqueue(new State(nr, nc, newDir));
                }
            }
        }

        return false;
    }

    static void Main()
    {
        int[,] maze = {
            {0,0,0,1},
            {1,0,1,0},
            {0,0,0,0},
            {0,1,0,0}
        };

        int sr = 0, sc = 0; // start
        int tr = 3, tc = 3; // truck destination

        Console.WriteLine(CanReach(maze, sr, sc, tr, tc)
            ? "Path exists!"
            : "No path found.");
    }
}

```


## traverse raod with block c# fucntion 

```
using System.Collections.Generic;

public class MazeSolver
{
    public static List<(int r, int c)> BFS(int[,] maze, (int r, int c) start, (int r, int c) goal)
    {
        int rows = maze.GetLength(0);
        int cols = maze.GetLength(1);

        var directions = new (int r, int c)[] 
        {
            (1,0), (-1,0), (0,1), (0,-1)
        };

        bool[,] visited = new bool[rows, cols];
        var queue = new Queue<(int r, int c)>();
        var parents = new Dictionary<(int r, int c), (int r, int c)>();

        queue.Enqueue(start);
        visited[start.r, start.c] = true;

        while (queue.Count > 0)
        {
            var (r, c) = queue.Dequeue();
            if ((r, c) == goal)
                return ReconstructPath(parents, goal);

            foreach (var (dr, dc) in directions)
            {
                int nr = r + dr;
                int nc = c + dc;

                if (nr >= 0 && nr < rows && nc >= 0 && nc < cols &&
                    maze[nr, nc] == 0 && !visited[nr, nc])
                {
                    visited[nr, nc] = true;
                    parents[(nr, nc)] = (r, c);
                    queue.Enqueue((nr, nc));
                }
            }
        }
        return null;
    }

    private static List<(int r, int c)> ReconstructPath(
        Dictionary<(int r, int c), (int r, int c)> parents,
        (int r, int c) goal)
    {
        var path = new List<(int r, int c)> { goal };
        var cur = goal;

        while (parents.ContainsKey(cur))
        {
            cur = parents[cur];
            path.Add(cur);
        }

        path.Reverse();
        return path;
    }
}

```

## Solve report based on Below output 


## Design hastable using array 


