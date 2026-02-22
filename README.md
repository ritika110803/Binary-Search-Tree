C Program: Binary Search Tree (BST) Implementation

This project demonstrates how to implement a *Binary Search Tree (BST)* in C with the following operations:

* Node Creation
* Insertion
* Inorder Traversal
* Searching

The program builds a BST and performs traversal and search operations.

---

Description

The program:

* Defines a BST node using struct
* Dynamically allocates memory using malloc()
* Inserts elements following BST rules:

  * Left subtree → values smaller than root
  * Right subtree → values greater than root
* Performs *Inorder Traversal* (which prints elements in sorted order)
* Searches for a specific value in the BST

This example is ideal for students learning *Binary Search Trees in Data Structures*.

---

Source Code

c

#include <stdio.h>

#include <stdlib.h>

// Structure of Node

struct Node {
    
    int data;
    struct Node* left;
    struct Node* right;
};

// Create new node

struct Node* createNode(int value) {
    
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
   
    newNode->data = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Insert into BST

struct Node* insert(struct Node* root, int value) {
    
    if (root == NULL)
        return createNode(value);

    if (value < root->data)
        root->left = insert(root->left, value);
    else if (value > root->data)
        root->right = insert(root->right, value);

    return root;
}

// Inorder Traversal (Sorted Order in BST)

void inorder(struct Node* root) {
    
    if (root != NULL) {
       
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

// Search in BST

struct Node* search(struct Node* root, int key) {
    
    if (root == NULL || root->data == key)
        return root;

    if (key < root->data)
        return search(root->left, key);
    else
        return search(root->right, key);
}

// Main function

int main() {
    
    struct Node* root = NULL;

    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 80);

    printf("Inorder Traversal (Sorted): ");
    inorder(root);

    int key = 40;
    
    if (search(root, key) != NULL)
        printf("\n%d found in BST", key);
    else
        printf("\n%d not found in BST", key);

    return 0;
}


---

How to Compile and Run

Using GCC

1. Save the file as bst.c
2. Open terminal or command prompt
3. Compile the program:


gcc bst.c -o bst


4. Run the executable:


./bst


(On Windows, use bst.exe)

---

Sample Output


Inorder Traversal (Sorted): 20 30 40 50 60 70 80
40 found in BST


---

Concepts Covered

* Binary Search Tree (BST)
* Recursive insertion
* Recursive search
* Inorder traversal
* Dynamic memory allocation
* Tree data structure

---

BST Rules

For every node:

* All values in the *left subtree* are smaller
* All values in the *right subtree* are larger

Because of this property, *Inorder Traversal prints elements in sorted order*.

---

Time Complexity

| Operation | Average Case | Worst Case |
| --------- | ------------ | ---------- |
| Insert    | O(log n)     | O(n)       |
| Search    | O(log n)     | O(n)       |
| Inorder   | O(n)         | O(n)       |

Worst case occurs when the BST becomes skewed.

---

Possible Improvements

* Add delete operation
* Implement level-order traversal
* Add height calculation
* Convert into menu-driven program
* Implement Balanced BST (AVL Tree)

---
