# DSA Using C Programs

This repository contains a collection of Data Structures and Algorithms (DSA) programs implemented in the C programming language.

## Table of Contents

1. [Matrix Transpose](#1-matrix-transpose)
2. [Polynomial Multiplication](#2-polynomial-multiplication)
3. [Polynomial Addition (2D)](#3-polynomial-addition-2d)
4. [Polynomial Addition and Subtraction](#4-polynomial-addition-and-subtraction)
5. [Stack Implementation](#5-stack-implementation)
6. [Balanced Parentheses](#6-balanced-parentheses)
7. [Reverse a String](#7-reverse-a-string)
8. [Postfix Expression Evaluation](#8-postfix-expression-evaluation)
9. [Prefix Expression Evaluation](#9-prefix-expression-evaluation)
10. [Infix to Postfix Conversion](#10-infix-to-postfix-conversion)
11. [Infix to Prefix Conversion](#11-infix-to-prefix-conversion)
12. [Queue Implementation](#12-queue-implementation)
13. [Circular Queue](#13-circular-queue)
14. [Insertion Sort](#14-insertion-sort)
15. [Bubble Sort](#15-bubble-sort)
16. [Selection Sort](#16-selection-sort)
17. [Linear Search](#17-linear-search)
18. [Binary Search](#18-binary-search)
19. [Linear Search on Sorted Data](#19-linear-search-on-sorted-data)
20. [Binary Search Tree](#20-binary-search-tree)

---

### 1. Matrix Transpose

```c
#include<stdio.h>

int main() {
    int matrix[2][2];
    int i, j;
    printf("Enter elements of 2 X 2 matrix:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            printf("Element [%d][%d]: ", i, j);
            scanf("%d", &matrix[i][j]);
        }
    }
    printf("\nOriginal Matrix:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            printf("%d\t", matrix[i][j]);
        }
        printf("\n");
    }
    printf("\nTranspose Matrix:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            printf("%d\t", matrix[j][i]);
        }
        printf("\n");
    }
    return 0;
}
```

---

### 2. Polynomial Multiplication

```c
#include<stdio.h>

void mult(int poly1[], int poly2[], int res[], int n1, int n2) {
    int i, j;
    for (i = 0; i < n1; i++) {
        for (j = 0; j < n2; j++) {
            res[i + j] += poly1[i] * poly2[j];
        }
    }
}

void disp(int poly[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("%d", poly[i]);
        if (i != n - 1) printf("x^%d", i);
        if (i != n - 1) printf("+");
    }
    printf("\n");
}

int main() {
    int n1, n2, poly1[100], poly2[100], i;
    printf("Enter number of terms in 1st Polynomial: ");
    scanf("%d", &n1);
    printf("Enter coefficients of 1st polynomial:\n");
    for (i = 0; i < n1; i++) {
        printf("Coefficient of x^%d: ", i);
        scanf("%d", &poly1[i]);
    }
    printf("Enter number of terms in 2nd Polynomial: ");
    scanf("%d", &n2);
    printf("Enter coefficients of 2nd polynomial:\n");
    for (i = 0; i < n2; i++) {
        printf("Coefficient of x^%d: ", i);
        scanf("%d", &poly2[i]);
    }
    int res[200] = {0};
    mult(poly1, poly2, res, n1, n2);
    printf("First Polynomial: ");
    disp(poly1, n1);
    printf("Second Polynomial: ");
    disp(poly2, n2);
    printf("After Multiplication: ");
    disp(res, n1 + n2 - 1);
    return 0;
}
```
---

### 3. Polynomial Addition (2D)

```c
#include<stdio.h>

void add(int poly1[][2], int poly2[][2], int res[][2], int n) {
    int i;
    for (i = 0; i < n; i++) {
        res[i][0] = poly1[i][0] + poly2[i][0];
    }
}

void disp(int poly[][2], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("%d", poly[i][0]);
        if (i != 0) printf("x^%d", i);
        if (i != n - 1) printf("+");
    }
    printf("\n");
}

int main() {
    int n, poly1[100][2], poly2[100][2], res[100][2], i;
    printf("Enter number of terms in the Polynomials: ");
    scanf("%d", &n);
    printf("Enter coefficients of 1st polynomial:\n");
    for (i = 0; i < n; i++) {
        printf("Coefficient of x^%d: ", i);
        scanf("%d", &poly1[i][0]);
    }
    printf("Enter coefficients of 2nd polynomial:\n");
    for (i = 0; i < n; i++) {
        printf("Coefficient of x^%d: ", i);
        scanf("%d", &poly2[i][0]);
    }
    add(poly1, poly2, res, n);
    printf("First Polynomial: ");
    disp(poly1, n);
    printf("Second Polynomial: ");
    disp(poly2, n);
    printf("After Addition: ");
    disp(res, n);
    return 0;
}
```

---

### 4. Polynomial Addition and Subtraction

```c
#include<stdio.h>

void add(int poly1[][2], int poly2[][2], int res1[][2], int n) {
    int i;
    for (i = 0; i < n; i++) {
        res1[i][0] = poly1[i][0] + poly2[i][0];
    }
}

void subs(int poly1[][2], int poly2[][2], int res2[][2], int n) {
    int i;
    for (i = 0; i < n; i++) {
        res2[i][0] = poly1[i][0] - poly2[i][0];
    }
}

void disp(int poly[][2], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("%d", poly[i][0]);
        if (i != 0) printf("x^%d", i);
        if (i != n - 1) printf("+");
    }
    printf("\n");
}

int main() {
    int n, poly1[100][2], poly2[100][2], res1[100][2], res2[100][2], i;
    printf("Enter number of terms in the Polynomials: ");
    scanf("%d", &n);
    printf("Enter coefficients of 1st polynomial:\n");
    for (i = 0; i < n; i++) {
        printf("Coefficient of x^%d: ", i);
        scanf("%d", &poly1[i][0]);
    }
    printf("Enter coefficients of 2nd polynomial:\n");
    for (i = 0; i < n; i++) {
        printf("Coefficient of x^%d: ", i);
        scanf("%d", &poly2[i][0]);
    }
    add(poly1, poly2, res1, n);
    subs(poly1, poly2, res2, n);
    printf("First Polynomial: ");
    disp(poly1, n);
    printf("Second Polynomial: ");
    disp(poly2, n);
    printf("After Addition: ");
    disp(res1, n);
    printf("After Subtraction: ");
    disp(res2, n);
    return 0;
}
```

---

### 5. Stack Implementation

```c
#include<stdio.h>
#define max 100

int top = -1;
int stack[max];

void push(int val) {
    if (top == max - 1) {
        printf("Cannot Push %d\n", val);
    } else {
        stack[++top] = val;
        printf("%d pushed to stack\n", val);
    }
}

void pop() {
    if (top == -1) {
        printf("Cannot Pop\n");
    } else {
        printf("%d popped from stack\n", stack[top--]);
    }
}

void peek() {
    if (top == -1) {
        printf("\nStack is Empty\n");
    } else {
        printf("Top element is %d\n", stack[top]);
    }
}

int isEmpty() {
    return top == -1;
}

int isFull() {
    return top == max - 1;
}

int main() {
    push(10);
    push(20);
    push(30);
    peek();
    pop();
    pop();
    peek();
    if (isEmpty()) {
        printf("\nStack is Empty\n");
    } else {
        printf("\nStack is not Empty\n");
    }
    if (isFull()) {
        printf("\nStack is Full\n");
    } else {
        printf("\nStack is not Full\n");
    }
    return 0;
}
```

---

### 6. Balanced Parentheses

```c
#include<stdio.h>
#include<string.h>
#define max 100

char stack[max];
int top;

void initStack() {
    top = -1;
}

void push(char item) {
    if (top == max - 1) {
        printf("Stack is Full\n");
    } else {
        stack[++top] = item;
    }
}

void pop() {
    if (top == -1) {
        printf("Stack is Empty\n");
    } else {
        --top;
    }
}

int isEmpty() {
    return top == -1;
}

int balancedParenthesis(char expression[]) {
    initStack();
    int i;
    for (i = 0; i < strlen(expression); i++) {
        char ch = expression[i];
        switch (ch) {
            case '(':
            case '{':
            case '[':
                push(ch);
                break;
            case ')':
                if (isEmpty() || stack[top] != '(') return 0;
                pop();
                break;
            case '}':
                if (isEmpty() || stack[top] != '{') return 0;
                pop();
                break;
            case ']':
                if (isEmpty() || stack[top] != '[') return 0;
                pop();
                break;
        }
    }
    return isEmpty();
}

int main() {
    char expression[max];
    printf("Enter an expression: ");
    scanf("%s", expression);
    if (balancedParenthesis(expression)) {
        printf("Parentheses are balanced.\n");
    } else {
        printf("Parentheses are not balanced.\n");
    }
    return 0;
}
```

---

### 7. Reverse a String Using Stack

```c
#include<stdio.h>
#include<string.h>
#define max 100

int top = -1, stack[max];

void push(char x) {
    if (top == max - 1) {
        printf("Stack is Full\n");
    } else {
        stack[++top] = x;
    }
}

void pop() {
    if (top == -1) {
        printf("Stack is Empty\n");
    } else {
        printf("%c", stack[top--]);
    }
}

int main() {
    char str[max];
    printf("Enter the string: ");
    scanf("%s", str);
    int len = strlen(str);
    int i;
    for (i = 0; i < len; i++) {
        push(str[i]);
    }
    printf("Reversed String: ");
    for (i = 0; i < len; i++) {
        pop();
    }
    return 0;
}
```

---

### 8. Evaluation of a Postfix Expression

```c
#include<stdio.h>
#include<ctype.h>
#include<string.h>
#define max 100

int stack[max];
int top = -1;

void push(int x) {
    if (top == max - 1) {
        printf("Stack is full\n");
    } else {
        stack[++top] = x;
    }
}

int pop() {
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    } else {
        return stack[top--];
    }
}

int performOperation(int op1, int op2, char operation) {
    switch (operation) {
        case '+': return op1 + op2;
        case '-': return op1 - op2;
        case '*': return op1 * op2;
        case '/': return op1 / op2;
        default: return 0;
    }
}

int evalPostfixExp(char *expression) {
    int l = strlen(expression);
    int i;
    for (i = 0; i < l; i++) {
        char c = expression[i];
        if (isdigit(c)) {
            push(c - '0');
        } else {
            int op2 = pop();
            int op1 = pop();
            int res = performOperation(op1, op2, c);
            push(res);
        }
    }
    return pop();
}

int main() {
    char expression[max];
    printf("Enter a postfix Expression: ");
    scanf("%s", expression);
    int res = evalPostfixExp(expression);
    printf("Result of Postfix Expression: %d\n", res);
    return 0;
}
```

---

### 9. Evaluation of a Prefix Expression

```c
#include<stdio.h>
#include<ctype.h>
#include<string.h>
#define max 100

int stack[max];
int top = -1;

void push(int x) {
    if (top == max - 1) {
        printf("Stack is full\n");
    } else {
        stack[++top] = x;
    }
}

int pop() {
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    } else {
        return stack[top--];
    }
}

int performOperation(int op1, int op2, char operation) {
    switch (operation) {
        case '+': return op1 + op2;
        case '-': return op1 - op2;
        case '*': return op1 * op2;
        case '/': return op1 / op2;
        default: return 0;
    }
}

int evalPrefixExp(char *expression) {
    int l = strlen(expression);
    int i;
    for (i = l - 1; i >= 0; i--) {
        char c = expression[i];
        if (isdigit(c)) {
            push(c - '0');
        } else {
            int op1 = pop();
            int op2 = pop();
            int res = performOperation(op1, op2, c);
            push(res);
        }
    }
    return pop();
}

int main() {
    char expression[max];
    printf("Enter a prefix Expression: ");
    scanf("%s", expression);
    int res = evalPrefixExp(expression);
    printf("Result of Prefix Expression: %d\n", res);
    return 0;
}
```

---

### 10. Infix to Postfix Conversion

```c
#include<stdio.h>
#include<string.h>
#define max 100

char stack[max];
int top = -1;

void push(char op) {
    if (top == max - 1) {
        printf("Stack is Full\n");
    } else {
        stack[++top] = op;
    }
}

char pop() {
    if (top == -1) {
        return -1;
    } else {
        return stack[top--];
    }
}

int precedence(char ch) {
    switch (ch) {
        case '+':
        case '-': return 1;
        case '*':
        case '/': return 2;
        case '^': return 3;
        default: return -1;
    }
}

void convertInfixToPostfix(char *expression) {
    int i, j = -1;
    char postfix[max];
    for (i = 0; expression[i]; ++i) {
        char c = expression[i];
        if ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9')) {
            postfix[++j] = c;
        } else if (c == '(') {
            push(c);
        } else if (c == ')') {
            while (top != -1 && stack[top] != '(') {
                postfix[++j] = pop();
            }
            pop();
        } else {
            while (top != -1 && precedence(c) <= precedence(stack[top])) {
                postfix[++j] = pop();
            }
            push(c);
        }
    }
    while (top != -1) {
        postfix[++j] = pop();
    }
    postfix[++j] = '\0';
    printf("Postfix Expression: %s\n", postfix);
}

int main() {
    char expression[max];
    printf("Enter an infix Expression: ");
    fgets(expression, max, stdin);
    expression[strcspn(expression, "\n")] = '\0';
    convertInfixToPostfix(expression);
    return 0;
}
```

---

### 11. Infix to Prefix Conversion

```c
#include<stdio.h>
#include<string.h>
#define max 100

char stack[max];
int top = -1;

void push(char op) {
    if (top == max - 1) {
        printf("Stack is Full\n");
    } else {
        stack[++top] = op;
    }
}

char pop() {
    if (top == -1) {
        return -1;
    } else {
        return stack[top--];
    }
}

int precedence(char ch) {
    switch (ch) {
        case '+':
        case '-': return 1;
        case '*':
        case '/': return 2;
        case '^': return 3;
        default: return -1;
    }
}

void reverse(char *expression) {
    int n = strlen(expression);
    int i;
    for (i = 0; i < n / 2; i++) {
        char temp = expression[i];
        expression[i] = expression[n - i - 1];
        expression[n - i - 1] = temp;
    }
}

void convertInfixToPrefix(char *expression) {
    reverse(expression);
    int i, j = 0;
    int n = strlen(expression);
    char result[max];
    memset(result, 0, sizeof(result));
    for (i = 0; expression[i]; ++i) {
        char c = expression[i];
        if (c == '(') {
            c = ')';
        } else if (c == ')') {
            c = '(';
        }
        if ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9')) {
            result[j++] = c;
        } else if (c == '(') {
            push(c);
        } else if (c == ')') {
            while (top != -1 && stack[top] != '(') {
                result[j++] = pop();
            }
            pop();
        } else {
            while (top != -1 && precedence(stack[top]) >= precedence(c)) {
                result[j++] = pop();
            }
            push(c);
        }
    }
    while (top != -1) {
        result[j++] = pop();
    }
    result[j] = '\0';
    reverse(result);
    printf("Prefix Expression: %s\n", result);
}

int main() {
    char expression[max];
    printf("Enter an infix Expression: ");
    fgets(expression, max, stdin);
    expression[strcspn(expression, "\n")] = '\0';
    convertInfixToPrefix(expression);
    return 0;
}
```

---

### 12. Queue Implementation

```c
#include<stdio.h>
#define size 5

int queue[size], front = -1, rear = -1;

void enqueue(int val) {
    if (rear == size - 1) {
        printf("Queue is Full!\n");
    } else {
        if (front == -1) {
            front = 0;
        }
        rear++;
        queue[rear] = val;
        printf("Inserted %d\n", val);
    }
}

void dequeue() {
    if (front == -1 || front > rear) {
        printf("Queue is Empty!\n");
    } else {
        printf("Deleted %d\n", queue[front]);
        front++;
    }
}

void display() {
    if (front == -1 || front > rear) {
        printf("Queue is Empty!\n");
    } else {
        printf("Queue elements are:\n");
        for (int i = front; i <= rear; i++) {
            printf("%d\t", queue[i]);
        }
        printf("\n");
    }
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();
    dequeue();
    display();
    return 0;
}
```

---

### 13. Circular Queue

```c
#include<stdio.h>
#define size 5

int cqueue[size], front = -1, rear = -1;

void enqueue(int val) {
    if ((rear + 1) % size == front) {
        printf("Circular Queue is Full!\n");
    } else {
        if (front == -1) {
            front = 0;
        }
        rear = (rear + 1) % size;
        cqueue[rear] = val;
        printf("Inserted %d\n", val);
    }
}

void dequeue() {
    if (front == -1) {
        printf("Circular Queue is Empty!\n");
    } else {
        printf("Deleted %d\n", cqueue[front]);
        if (front == rear) {
            front = -1;
            rear = -1;
        } else {
            front = (front + 1) % size;
        }
    }
}

void display() {
    if (front == -1) {
        printf("Circular Queue is Empty!\n");
    } else {
        printf("Circular Queue Elements are:\n");
        int i;
        for (i = front; i != rear; i = (i + 1) % size) {
            printf("%d\t", cqueue[i]);
        }
        printf("%d\n", cqueue[rear]);
    }
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();
    dequeue();
    display();
    return 0;
}
```

---

### 14. Insertion Sort

```c
#include<stdio.h>

int main() {
    int A[6] = {18, 7, 22, 3, 14, 2};
    int i, j, key;
    printf("Before Sorting: ");
    for (i = 0; i < 6; i++) {
        printf("%d\t", A[i]);
    }
    printf("\n");
    for (i = 1; i < 6; i++) {
        key = A[i];
        for (j = i - 1; j >= 0 && A[j] > key; j--) {
            A[j + 1] = A[j];
        }
        A[j + 1] = key;
    }
    printf("After Sorting: ");
    for (i = 0; i < 6; i++) {
        printf("%d\t", A[i]);
    }
    printf("\n");
    return 0;
}
```

---

### 15. Bubble Sort

```c
#include<stdio.h>

int main() {
    int A[5] = {64, 34, 25, 12, 22};
    int i, j, temp;
    printf("Before Sorting: ");
    for (i = 0; i < 5; i++) {
        printf("%d\t", A[i]);
    }
    printf("\n");
    for (i = 0; i < 4; i++) {
        for (j = 0; j < 4 - i; j++) {
            if (A[j] > A[j + 1]) {
                temp = A[j];
                A[j] = A[j + 1];
                A[j + 1] = temp;
            }
        }
    }
    printf("After Sorting: ");
    for (i = 0; i < 5; i++) {
        printf("%d\t", A[i]);
    }
    printf("\n");
    return 0;
}
```

### 16. Selection Sort

```c
#include<stdio.h>

int main() {
    int A[5] = {12, 11, 13, 5, 6};
    int i, j, minIdx, temp;
    printf("Before Sorting: ");
    for (i = 0; i < 5; i++) {
        printf("%d\t", A[i]);
    }
    printf("\n");
    for (i = 0; i < 4; i++) {
        minIdx = i;
        for (j = i + 1; j < 5; j++) {
            if (A[j] < A[minIdx]) {
                minIdx = j;
            }
        }
        temp = A[minIdx];
        A[minIdx] = A[i];
        A[i] = temp;
    }
    printf("After Sorting: ");
    for (i = 0; i < 5; i++) {
        printf("%d\t", A[i]);
    }
    printf("\n");
    return 0;
}
```

---

### 17. Linear Search

```c
#include<stdio.h>

int linearSearch(int arr[], int target) {
    for (int i = 0; i < 5; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}

int main() {
    int arr[5] = {10, 2, 8, 5, 17};
    int target;
    printf("Enter the value to search: ");
    scanf("%d", &target);
    int result = linearSearch(arr, target);
    if (result == -1) {
        printf("Element not found in the array.\n");
    } else {
        printf("Element %d found at index %d.\n", target, result);
    }
    return 0;
}
```

---

### 18. Binary Search

```c
#include<stdio.h>
#define size 8

int binarySearch(int arr[], int target) {
    int low = 0, high = size - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}

int main() {
    int arr[size] = {1, 3, 5, 7, 9, 11, 13, 15};
    int target;
    printf("Enter the target value: ");
    scanf("%d", &target);
    int result = binarySearch(arr, target);
    if (result != -1) {
        printf("Element %d found at index %d.\n", target, result);
    } else {
        printf("Element %d not found.\n", target);
    }
    return 0;
}
```

---

### 19. Linear Search on Sorted Data

```c
#include<stdio.h>
#define size 5

int main() {
    int A[size], x, i;
    printf("Enter %d elements in sorted order:\n", size);
    for (i = 0; i < size; i++) {
        printf("Element %d: ", i + 1);
        scanf("%d", &A[i]);
    }
    printf("Enter value to search: ");
    scanf("%d", &x);
    for (i = 0; i < size; i++) {
        if (A[i] == x) {
            printf("Value found at index %d.\n", i);
            return 0;
        } else if (A[i] > x) {
            break;
        }
    }
    printf("Value not found.\n");
    return 0;
}
```

---

### 20. Binary Search Tree (BST) - Add, Search, Min, Max

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int key) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->key = key;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* add(struct Node* root, int key) {
    if (root == NULL) {
        return createNode(key);
    }
    if (key < root->key) {
        root->left = add(root->left, key);
    } else if (key > root->key) {
        root->right = add(root->right, key);
    }
    return root;
}

int search(struct Node* root, int key) {
    if (root == NULL) {
        return 0;
    }
    if (root->key == key) {
        return 1;
    }
    if (key < root->key) {
        return search(root->left, key);
    } else {
        return search(root->right, key);
    }
}

struct Node* findMin(struct Node* root) {
    while (root && root->left != NULL) {
        root = root->left;
    }
    return root;
}

struct Node* findMax(struct Node* root) {
    while (root && root->right != NULL) {
        root = root->right;
    }
    return root;
}

int main() {
    struct Node* root = NULL;
    int ch, val;
    while (1) {
        printf("\n1. Add\n2. Search\n3. Min\n4. Max\n5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                printf("Enter value to add: ");
                scanf("%d", &val);
                root = add(root, val);
                break;
            case 2:
                printf("Enter value to search: ");
                int value;
                scanf("%d", &value);
                if (search(root, value)) {
                    printf("Value %d found in the BST.\n", value);
                } else {
                    printf("Value %d not found in the BST.\n", value);
                }
                break;
            case 3:
                if (root) {
                    printf("Minimum value in the BST: %d\n", findMin(root)->key);
                } else {
                    printf("The tree is empty.\n");
                }
                break;
            case 4:
                if (root) {
                    printf("Maximum value in the BST: %d\n", findMax(root)->key);
                } else {
                    printf("The tree is empty.\n");
                }
                break;
            case 5:
                exit(0);
            default:
                printf("Invalid choice.\n");
        }
    }
    return 0;
}
```

---

### 21. Binary Search Tree (BST) - Create, Insert, Count Leaf Nodes, Count Total Nodes, and Depth

```c
#include<stdio.h>
#include<stdlib.h>

struct Node {
    int data;
    struct Node *left;
    struct Node *right;
};

struct Node *createNode(int val) {
    struct Node *newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node *insert(struct Node *root, int val) {
    if (root == NULL) {
        return createNode(val);
    }
    if (val < root->data) {
        root->left = insert(root->left, val);
    } else if (val > root->data) {
        root->right = insert(root->right, val);
    }
    return root;
}

int countNodes(struct Node *root) {
    if (root == NULL) {
        return 0;
    }
    return 1 + countNodes(root->left) + countNodes(root->right);
}

int countLeaf(struct Node *root) {
    if (root == NULL) {
        return 0;
    }
    if (root->left == NULL && root->right == NULL) {
        return 1;
    }
    return countLeaf(root->left) + countLeaf(root->right);
}

int depth(struct Node *root) {
    if (root == NULL) {
        return 0;
    }
    int leftDepth = depth(root->left);
    int rightDepth = depth(root->right);
    return 1 + (leftDepth > rightDepth ? leftDepth : rightDepth);
}

void inorder(struct Node *root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d\t", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node *root = NULL;
    int ch, val;
    while (1) {
        printf("\n1. Insert\n2. Display (Inorder)\n3. Count Nodes\n4. Count Leaf Nodes\n5. Depth\n6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &val);
                root = insert(root, val);
                break;
            case 2:
                printf("Inorder Traversal: ");
                inorder(root);
                printf("\n");
                break;
            case 3:
                printf("Total number of nodes: %d\n", countNodes(root));
                break;
            case 4:
                printf("Total number of leaf nodes: %d\n", countLeaf(root));
                break;
            case 5:
                printf("Depth (Height): %d\n", depth(root));
                break;
            case 6:
                exit(0);
            default:
                printf("Invalid choice.\n");
        }
    }
    return 0;
}
```

---

### 22. Bubble Sort (Alternate Implementation)

```c
#include<stdio.h>

void bubbleSort(int arr[], int n) {
    int i, j, temp;
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d\t", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {5, 3, 8, 4, 2};
    int n = sizeof(arr) / sizeof(arr[0]);
    printf("Before Sorting: ");
    printArray(arr, n);
    bubbleSort(arr, n);
    printf("After Sorting: ");
    printArray(arr, n);
    return 0;
}
```

---

### 23. Insertion Sort (Alternate Implementation)

```c
#include<stdio.h>

void insertionSort(int arr[], int n) {
    int i, j, key;
    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d\t", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {10, 5, 3, 8, 15};
    int n = sizeof(arr) / sizeof(arr[0]);
    printf("Before Sorting: ");
    printArray(arr, n);
    insertionSort(arr, n);
    printf("After Sorting: ");
    printArray(arr, n);
    return 0;
}
```

---
