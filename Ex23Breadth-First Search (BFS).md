# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE: 26.07.2026
## AIM:
To design and implement a java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm
1. Import the necessary libraries.
2. Create a graph structure with List<List<Integer>>.
3. Define a method addEdge to insert the vertices and edges into the List.
4. Define a bfs method to perfrom breadth First Search.
5. Use a Queue to implement bfs.
6. Display the results.

## Program:
```
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: Ashqar Ahamed S T
RegisterNumber: 212224240018
*/

import java.util.*;

public class EmergencyRouteBFS {
    public static void addEdge(List<List<Integer>> g, int u, int v) {
         //Type your Code
         g.get(u).add(v);
         g.get(v).add(u);
    }

    public static void bfs(List<List<Integer>> g, int src, boolean[] visited) {
        //Type your Code
        
        Queue<Integer> queue = new LinkedList<>();
        List<Integer> res = new ArrayList<>();
        
        queue.add(src);
        visited[src] = true;
        
        while(!queue.isEmpty())
        {
            int val = queue.poll();
            res.add(val);
            for(int j : g.get(val))
            {
                if(!visited[j])
                {
                    visited[j] = true;
                    queue.add(j);
                }
            }
        }
        
        for(int r: res)
            System.out.print(r + " ");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), e = sc.nextInt();
        List<List<Integer>> g = new ArrayList<>();
        for (int i = 0; i < n; i++) g.add(new ArrayList<>());
        for (int i = 0; i < e; i++) addEdge(g, sc.nextInt(), sc.nextInt());
        int src = sc.nextInt();
        bfs(g, src, new boolean[n]);
    }
}

```

## Output:

<img width="572" height="327" alt="output Day3" src="https://github.com/user-attachments/assets/c3e03031-efc7-46ab-ad41-1affc3e64755" />


## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
