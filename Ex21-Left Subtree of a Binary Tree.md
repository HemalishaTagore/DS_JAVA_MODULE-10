# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE: 05/09/2026
## AIM:
To design and implement a java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm

1. Start the program.
2. Read the elements in level order and construct the binary tree.
3. Find the left child of the root node.
4. Recursively count all nodes in the left subtree.
5. Display the number of nodes in the left subtree and stop the program.
## Program:
```
/*
Program to construct a binary tree from level order input and count the number of nodes
in the left subtree of the root node.
Developed by: HEMALISHA T
RegisterNumber: 212225040123
*/

import java.util.*;

class LeftSubtreeCount {

    static class Node {
        int data;
        Node left, right;

        Node(int data) {
            this.data = data;
        }
    }

    static int countNodes(Node root) {
        if (root == null)
            return 0;

        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    static Node buildTree(int arr[]) {

        if (arr.length == 0)
            return null;

        Node root = new Node(arr[0]);

        Queue<Node> queue = new LinkedList<>();
        queue.add(root);

        int i = 1;

        while (i < arr.length) {

            Node current = queue.poll();

            if (i < arr.length) {
                current.left = new Node(arr[i++]);
                queue.add(current.left);
            }

            if (i < arr.length) {
                current.right = new Node(arr[i++]);
                queue.add(current.right);
            }
        }

        return root;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        int arr[] = new int[n];

        System.out.println("Enter level order elements:");

        for (int i = 0; i < n; i++)
            arr[i] = sc.nextInt();

        Node root = buildTree(arr);

        int count = countNodes(root.left);

        System.out.println("Number of nodes in left subtree: " + count);

        sc.close();
    }
}
```

## Output:

<img width="396" height="278" alt="image" src="https://github.com/user-attachments/assets/723aa8c1-41d4-46d6-8c3b-edf2addf45a7" />



## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
