# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm
## DATE: 01.09.2026
## AIM:
To design and implement a java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Import the necessary libraries.
2. Initialize a graph with given vertices and edges, Add vertex and wieght as a node. 
3. Define a method to implement Dijkstra's Algorithm.
4. Implement a PriorityQueue<> to add vertices with lowest wieght with heighest priority.
5. Find the shortest distance from source to destination.
6. Return the distance.

## Program:
```
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: Ashqar Ahamed S T
RegisterNumber: 212224240018
*/

import java.util.*;

public class EVChargingNavigation {

    static class Pair {
        int node, time;
        Pair(int node, int time) {
            this.node = node;
            this.time = time;
        }
    }

    static int findNearestChargingStation(int n, List<List<Pair>> graph, int source, Set<Integer> stations) {
        //Type your code
        int[] TIME = new int[n];
        PriorityQueue<Pair> pq = new PriorityQueue<>((a,b) -> a.time - b.time);
        
        Arrays.fill(TIME, Integer.MAX_VALUE);
        
        TIME[source] = 0;
        pq.add(new Pair(source,0));
        
        while(!pq.isEmpty())
        {
            Pair curr = pq.poll();
            int u = curr.node;
            int currtime = curr.time;
            
            if(stations.contains(u))
            {
                return TIME[u];
            }
            
            for(Pair neighbour : graph.get(u))
            {
                int v = neighbour.node;
                int time = neighbour.time;
                
                int newtime = currtime + time;
                
                if(newtime < TIME[v])
                {
                    TIME[v] = newtime;
                    pq.add(new Pair(v, newtime));
                }
            }
        }
        
        return -1;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt(), m = sc.nextInt();
        List<List<Pair>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        for (int i = 0; i < m; i++) {
            int u = sc.nextInt(), v = sc.nextInt(), w = sc.nextInt();
            graph.get(u).add(new Pair(v, w));
            graph.get(v).add(new Pair(u, w)); // Undirected
        }

        int source = sc.nextInt();
        int k = sc.nextInt();
        Set<Integer> stations = new HashSet<>();
        for (int i = 0; i < k; i++) stations.add(sc.nextInt());

        System.out.println(findNearestChargingStation(n, graph, source, stations));
    }
}

```

## Output:

<img width="477" height="400" alt="output Day5" src="https://github.com/user-attachments/assets/bcb3e664-25e9-4434-8ef1-f58546f22824" />


## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
