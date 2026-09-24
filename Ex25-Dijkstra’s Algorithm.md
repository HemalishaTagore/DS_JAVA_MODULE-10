# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm
## DATE: 05/09/2026
## AIM:
To design and implement a java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Start.
2. Read the number of blocks, travel times, starting block, and charging stations.
3. Initialize distances with infinity and set the starting block distance as 0.
4. Use Dijkstra’s algorithm to find the shortest travel time to every reachable block.
5. Find and display the nearest charging station with minimum travel time, then stop.

## Program:
```
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: HEMALISHA T
RegisterNumber: 212225040123
*/

import java.util.*;

public class ChargingStationDijkstra {

    static final int INF = 999999;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of blocks: ");
        int n = sc.nextInt();

        int[][] graph = new int[n][n];

        System.out.println("Enter travel time matrix (0 for no path):");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                graph[i][j] = sc.nextInt();
            }
        }

        System.out.print("Enter current block: ");
        int source = sc.nextInt();

        System.out.print("Enter number of charging stations: ");
        int s = sc.nextInt();

        int[] stations = new int[s];

        System.out.println("Enter charging station blocks:");
        for (int i = 0; i < s; i++) {
            stations[i] = sc.nextInt();
        }

        int[] dist = new int[n];
        boolean[] visited = new boolean[n];

        Arrays.fill(dist, INF);
        dist[source] = 0;

        for (int count = 0; count < n; count++) {
            int u = -1;
            int min = INF;

            for (int i = 0; i < n; i++) {
                if (!visited[i] && dist[i] < min) {
                    min = dist[i];
                    u = i;
                }
            }

            if (u == -1)
                break;

            visited[u] = true;

            for (int v = 0; v < n; v++) {
                if (graph[u][v] > 0 && !visited[v]) {
                    int newDist = dist[u] + graph[u][v];

                    if (newDist < dist[v]) {
                        dist[v] = newDist;
                    }
                }
            }
        }

        int nearest = -1;
        int shortestTime = INF;

        for (int station : stations) {
            if (dist[station] < shortestTime) {
                shortestTime = dist[station];
                nearest = station;
            }
        }

        if (nearest == -1 || shortestTime == INF) {
            System.out.println("No charging station is reachable.");
        } else {
            System.out.println("Nearest charging station: " + nearest);
            System.out.println("Shortest travel time: " + shortestTime);
        }

        sc.close();
    }
}
```

## Output:



<img width="460" height="465" alt="image" src="https://github.com/user-attachments/assets/7a267c39-1940-4040-870e-75721d0e7f35" />



## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
