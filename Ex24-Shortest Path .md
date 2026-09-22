# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE: 28.07.2026
## AIM:
To design and implement a java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm
1. Import necessary libraries
2. Define the method shortestPath() to perform Breadth First Search to find the shortest path from the starting point to the Destination.
3. Define a method reachableAttractions to perform Depth First Search to find all the reachable locations.
4. Count the reachable locations by counting the visited nodes from DFS.
5. Display the results.

## Program:
```
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: Ashqar Ahamed S T
RegisterNumber: 212224240018
*/

import java.util.*;

public class TouristNavigation {
    
    public static int shortestPath(List<List<Integer>> graph, int start, int target, int n) {
      //Type your code
      Queue<Integer> queue = new LinkedList<>();
      boolean[] visited = new boolean[n];
      int[] distance = new int[n];
      
      queue.add(start);
      visited[start] = true;
      distance[start] = 0;
      
      while(!queue.isEmpty())
      {
          int val = queue.poll();
          if(val == target)
          {
              return distance[val];
          }
          
          for(int neighbour : graph.get(val))
          {
              if(!visited[neighbour])
              {
                  visited[neighbour] = true;
                  distance[neighbour] = distance[val] + 1;
                  queue.add(neighbour);
              }
          }
      }
      return -1;
    }

    public static void reachableAttractions(List<List<Integer>> graph, boolean[] visited, int node) {
        //Type your code  
        
        visited[node] = true;
        for(int neighbour : graph.get(node))
        {
            if(!visited[neighbour])
            {
                reachableAttractions(graph, visited, neighbour);
            }
        }
    }

    public static int countReachable(boolean[] visited) {
        //Type your code
        int count = 0;
        for(boolean val : visited)
        {
            if(val)
                count++;
        }
        return count;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), e = sc.nextInt();
        List<List<Integer>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        for (int i = 0; i < e; i++) {
            int u = sc.nextInt(), v = sc.nextInt();
            graph.get(u).add(v);
            graph.get(v).add(u);
        }

        int start = sc.nextInt();
        int target = sc.nextInt();

        int shortest = shortestPath(graph, start, target, n);
        boolean[] visited = new boolean[n];
        reachableAttractions(graph, visited, start);
        int reachable = countReachable(visited);

        System.out.println("Shortest path from start to target: " + shortest);
        System.out.println("Total reachable attractions from start: " + reachable);
    }
}

```

## Output:

<img width="1120" height="352" alt="output Day4" src="https://github.com/user-attachments/assets/eb52ceb9-197d-4899-be8f-6fcebd68314d" />


## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
