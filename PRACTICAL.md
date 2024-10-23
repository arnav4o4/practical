# SORTING:

```c
// ! SORTING - INSERTION AND BUBBLE SORT
#include <stdio.h>

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90}; // Sample unsorted array
    int size = 7; //sizeof(arr) / sizeof(arr[0]); // Calculate the size of the array
    int arrCopy[size]; // Array to hold a copy for bubble sort

    // Copy original array to arrCopy for bubble sort
    for (int i = 0; i < size; i++) {
        arrCopy[i] = arr[i];
    }

    // Insertion Sort
    for (int i = 1; i < size; i++) {                ------- > NOTE !!!
        int key = arr[i];
        int j = i - 1;

        // Move elements of arr[0..i-1] that are greater than key
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key; // Insert the key at the correct position
    }

    // Print the sorted array using Insertion Sort
    printf("Sorted array using Insertion Sort: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

// ! -------------------------------------------------------------------------------
    // Bubble Sort
    for (int i = 0; i < size - 1; i++) {
        for (int j = 0; j < size - i - 1; j++) {      ------- > NOTE !!!
            // Swap if the element found is greater than the next element
            if (arrCopy[j] > arrCopy[j + 1]) {
                // Swap the elements
                int temp = arrCopy[j];
                arrCopy[j] = arrCopy[j + 1];
                arrCopy[j + 1] = temp;
            }
        }
    }

    // Print the sorted array using Bubble Sort
    printf("Sorted array using Bubble Sort: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arrCopy[i]);
    }
    printf("\n");
    return 0;
}
```

# Searching:

```c
int main()
{
    int arr[] = {5, 3, 8, 4, 2}; // Sample array
    int size = 5;                // sizeof(arr) / sizeof(arr[0]); // Calculate the size of the array
    int target = 3;

    // Perform linear search
    for (int i = 0; i < size; i++)
    {
        if (arr[i] == target)
        {
            printf("Element %d found at index %d.\n", target, i);
            exit(0); // *Exit the the program once the element is found
        }
    }
    printf("Element %d not found in the array.\n", target);

    return 0;
}
```

# matrix multiplication

```c
//! MATRIX MULTIPLICATION
// C program to multiply two matrices

#include <stdio.h>
#include <stdlib.h>

void mulMat(int r1, int c1, int r2, int c2, int mat1[][c1], int mat2[][c2])
{
    int rslt[r1][c2];

    printf("Multiplication of given two matrices is:\n");

    for (int i = 0; i < r1; i++)
    {
        for (int j = 0; j < c2; j++)
        {
            rslt[i][j] = 0;

            for (int k = 0; k < c1; k++)
            {
                rslt[i][j] += mat1[i][k] * mat2[k][j];
            }

            printf("%d\t", rslt[i][j]);
        }

        printf("\n");
    }
}

// Driver code
int main()
{
    int r1 = 2, c1 = 2, r2 = 2, c2 = 2;

    int mat1[2][2] = {{1, 1}, {2, 2}};

    int mat2[2][2] = {{1, 1}, {2, 2}};

    if (c1 != r2)
    {
        printf("The number of columns in Matrix-1 must be "
               "equal to the number of rows in "
               "Matrix-2\n");

        exit(EXIT_FAILURE);
    }

    // Function call
    mulMat(r1, c1, r2, c2, mat1, mat2);

    return 0;
}

```



# BT

```c
#include <stdio.h>
#define MAX 15
int tree[MAX] = {0}; // Initialize tree array with 0
void insert(int data, int position)
{
    if (position >= MAX)
    {
        printf("Position out of bounds!\n");
    }
    else
    {
        tree[position] = data;
        printf("Inserted %d at position %d\n", data, position);
    }
}
void display()
{
    int i;
    printf("Tree elements:\n");
    for (i = 1; i < MAX; i++)               ------------> NOTE!!!
    {
        if (tree[i] != 0)
        {
            printf("Position %d: %d\n", i, tree[i]);
        }
    }
}
int main()
{
    insert(1, 1); // Root node
    insert(2, 2); // Left child of root
    insert(3, 3); // Right child of rootinsert(4, 4); // Left child of node 2
    insert(5, 5); // Right child of node 2
    insert(6, 6); // Left child of node 3
    insert(7, 7); // Right child of node 3
    display();
    return 0;
}
```

# adjacency matrix

```c
#include <stdio.h>
#define MAX 10
int adjMatrix[MAX][MAX];
int n;

void initGraph(int vertices)
{
    n = vertices;
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(int u, int v)
{
    adjMatrix[u][v] = 1;
    adjMatrix[v][u] = 1;
}

void displayGraph()
{
    printf("Adjacency Matrix:\n");
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("%d ", adjMatrix[i][j]);
        }
        printf("\n");
    }
}
int main()
{
    int vertices, u, v;
    printf("Enter the number of vertices: ");
    scanf("%d", &vertices);

    initGraph(vertices);

    printf("Enter edge (u v): ");
    scanf("%d %d", &u, &v);

    if (u < vertices && v < vertices)
    {
        addEdge(u, v);
    }
    else
    {
        printf("Invalid vertices!\n");
    }

    displayGraph();
    return 0;
}
```
