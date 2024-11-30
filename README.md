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
