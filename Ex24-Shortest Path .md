# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE:
## AIM:
To design and implement a java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm
1. Start.
2. Read the number of attractions and their connections in the graph.
3. Start BFS from the given source and store the distance of each attraction.
4. Find the distance of the target attraction and count all reachable attractions.
5. Display the shortest number of paths and reachable attractions, then stop.

## Program:
```
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: HEMALISHA T
RegisterNumber: 212225040123
*/

import java.util.*;

public class HeritageBFS {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of attractions: ");
        int n = sc.nextInt();

        int[][] graph = new int[n][n];

        System.out.println("Enter adjacency matrix:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                graph[i][j] = sc.nextInt();
            }
        }

        System.out.print("Enter starting attraction: ");
        int source = sc.nextInt();

        System.out.print("Enter target attraction: ");
        int target = sc.nextInt();

        boolean[] visited = new boolean[n];
        int[] distance = new int[n];

        Queue<Integer> queue = new LinkedList<>();

        visited[source] = true;
        distance[source] = 0;
        queue.add(source);

        int reachable = 0;

        while (!queue.isEmpty()) {
            int current = queue.poll();
            reachable++;

            for (int i = 0; i < n; i++) {
                if (graph[current][i] == 1 && !visited[i]) {
                    visited[i] = true;
                    distance[i] = distance[current] + 1;
                    queue.add(i);
                }
            }
        }

        if (visited[target]) {
            System.out.println("Shortest path: " + distance[target] + " hops");
        } else {
            System.out.println("Target attraction is not reachable");
        }

        System.out.println("Reachable attractions: " + reachable);

        sc.close();
    }
}
```

## Output:

![Uploading image.png…]()


## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
