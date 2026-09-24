# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE: 05/09/2026
## AIM:
To design and implement a java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm

1. Start.
2. Read the number of junctions and their connections in the graph.
3. Create a queue and mark the source junction as visited.
4. Remove a junction from the queue, print it, and add all unvisited adjacent junctions.
5. Repeat until the queue is empty and stop.
## Program:
```
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: HEMALISHA T
RegisterNumber: 212225040123
*/

import java.util.*;

public class BFS {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of junctions: ");
        int n = sc.nextInt();

        int[][] graph = new int[n][n];

        System.out.println("Enter adjacency matrix:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                graph[i][j] = sc.nextInt();
            }
        }

        System.out.print("Enter source junction: ");
        int source = sc.nextInt();

        boolean[] visited = new boolean[n];
        Queue<Integer> queue = new LinkedList<>();

        visited[source] = true;
        queue.add(source);

        System.out.print("BFS Traversal: ");

        while (!queue.isEmpty()) {
            int current = queue.poll();
            System.out.print(current + " ");

            for (int i = 0; i < n; i++) {
                if (graph[current][i] == 1 && !visited[i]) {
                    visited[i] = true;
                    queue.add(i);
                }
            }
        }

        sc.close();
    }
}
```

## Output:

<img width="470" height="373" alt="image" src="https://github.com/user-attachments/assets/749bb68d-3e2a-4bc5-8d72-4518ad939985" />


## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
