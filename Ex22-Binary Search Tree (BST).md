# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE:
## AIM:
To design and implement java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Start the program.
2. Read the Book IDs and insert them into a Binary Search Tree.
3. Read the Book ID to be searched.
4. Compare the search ID with the current node and move left or right accordingly.
5. Display whether the Book ID exists in the BST and stop the program.

## Program:
```
/*
Program to construct a Binary Search Tree using given Book IDs
and search for a specific Book ID.
Developed by: HEMALISHA T
RegisterNumber: 212225040123
*/

import java.util.Scanner;

class BookBST {

    static class Node {
        int data;
        Node left, right;

        Node(int data) {
            this.data = data;
        }
    }

    static Node insert(Node root, int data) {

        if (root == null)
            return new Node(data);

        if (data < root.data)
            root.left = insert(root.left, data);
        else if (data > root.data)
            root.right = insert(root.right, data);

        return root;
    }

    static boolean search(Node root, int key) {

        if (root == null)
            return false;

        if (root.data == key)
            return true;

        if (key < root.data)
            return search(root.left, key);
        else
            return search(root.right, key);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        Node root = null;

        System.out.print("Enter number of Book IDs: ");
        int n = sc.nextInt();

        System.out.println("Enter Book IDs:");

        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }

        System.out.print("Enter Book ID to search: ");
        int key = sc.nextInt();

        if (search(root, key))
            System.out.println("Book ID " + key + " exists in the BST.");
        else
            System.out.println("Book ID " + key + " does not exist in the BST.");

        sc.close();
    }
}
```

## Output:


<img width="295" height="264" alt="image" src="https://github.com/user-attachments/assets/f6df1cbd-579b-4f74-802c-6d141c46efc8" />

## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
