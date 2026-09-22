# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE: 25.07.2026
## AIM:
To design and implement java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Import the necessary Libraries.
2. Define methods required to implement a Binary Search Tree with doubly linked list such as insert.
3. Define a method to search a value in the tree.
4. Call the search function to find if the target Book ID exists
5. Return true if it exists else false.

## Program:
```
/*
Program to constructs a Binary Search Tree (BST) using given Book IDs 
Developed by: Ashqar Ahamed S T
RegisterNumber: 212224240018
*/

import java.util.*;

public class BookIDSearch {
    

    public static Node insert(Node root, int key) {
         
         if(root == null)
            return new Node(key);
        
        if(key < root.data)
            root.left = insert(root.left,key);
        else if (key > root.data)
            root.right = insert(root.right,key);
            
        return root;
    }

    public static boolean search(Node root, int key) {
        
        if(root==null)
            return false;
            
        if(key<root.data)
            return search(root.left,key);
        else if (key > root.data)
            return search(root.right,key);
        else
            return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Node root = null;
        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }
        int q = sc.nextInt();
        while (q-- > 0) {
            int key = sc.nextInt();
            System.out.println(search(root, key) ? "Found" : "Not Found");
        }
    }
}
class Node {
        int data;
        Node left, right;
        Node(int data) {
            this.data = data;
        }
    }


```

## Output:

<img width="763" height="286" alt="output Day2" src="https://github.com/user-attachments/assets/f42ad35e-b43e-4ac8-9fa1-a0ca82806cb5" />


## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
