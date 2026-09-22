# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE: 24.07.2026
## AIM:
To design and implement a java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm
1. Import the necessary Libraries.
2. Define a method buildTree to construct a tree structure with double linked list.
3. Construct a method to find the number of nodes in the tree.
4. while adding the first node to the queue, add the node root.left to find the subnodes of int the left side.
5. Display the count.

## Program:
```
/*
Program to constructs a binary tree from given level order input and counts the number of nodes 
Developed by: Ashqar Ahamed S T
RegisterNumber: 212224240018
*/

import java.util.*;

class Node {
   //Type your code
   int data;
   Node left, right;
   
   Node(int val)
   {
       this.data = val;
       left = right = null;
   }
}

public class Main {
    static Node buildTree(int[] arr) {
       //Type your code
       
       if(arr.length == 0 || arr[0] == -1)
            return null;
            
        Node root = new Node(arr[0]);
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        int i = 1;
        
        while(i<arr.length && !q.isEmpty())
        {
            Node current = q.poll();
            
            if(i < arr.length && arr[i] != -1)
            {
                current.left = new Node(arr[i]);
                q.add(current.left);
            }
            i++;
            
            if(i<arr.length && arr[i] != -1)
            {
                current.right = new Node(arr[i]);
                q.add(current.right);
            }
            i++;
        }
        
        return root;
    }
    
    

    static void countNodes(Node root) {
    //Type your code
    
        if(root == null || root.left == null)
        {
            System.out.println(0);
            return;
        }
        
        Queue<Node> q = new LinkedList<>();
        q.add(root.left);
        
        int count = 0;
        
        while(!q.isEmpty())
        {
            Node current = q.poll();
            count++;
            if(current.left!=null)
                q.add(current.left);
                
            if (current.right != null)
                q.add(current.right);
        }
        
        System.out.println(count);
    
    }


    public static void main(String[] args) {
      //Type yo
      
      Scanner sc = new Scanner(System.in);
      int n = sc.nextInt();
      int[] arr = new int[n];
      for(int i=0;i<n;i++)
        arr[i] = sc.nextInt();
        
        Node root = buildTree(arr);
        countNodes(root);
        
    }
}
```

## Output:

<img width="530" height="211" alt="output Day1" src="https://github.com/user-attachments/assets/a2f36081-ea29-4cdc-9751-d620b3518697" />


## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
