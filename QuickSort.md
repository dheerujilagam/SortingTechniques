# Quick Sort
Quicksort is a highly efficient and widely used sorting algorithm based on the divide-and-conquer strategy. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, one with elements less than the pivot and the other with elements greater than the pivot. The sub-arrays are then sorted recursively. Quicksort is known for its average-case time complexity of O(n log n), making it one of the fastest sorting algorithms.

# Algorithm
    1. Choose a pivot element from the array.
    2. Partition the array into two sub-arrays: elements less than the pivot and elements greater than the pivot.
    3. Recursively apply the Quicksort algorithm to the two sub-arrays.
    4. Concatenate the sorted sub-arrays and the pivot element.

# Example
Let's work through an example using the input array [45, 23, 11, 89, 77, 98, 4, 28].

Step 1: Choose a pivot. For this example, let's choose the last element, 28.

Step 2: Partition the array around the pivot.

    Array: [45, 23, 11, 89, 77, 98, 4, 28]
    
    Partitioning:
    
    Elements less than 28: [23, 11, 4]
    Pivot: 28
    Elements greater than 28: [45, 89, 77, 98]

Step 3: Recursively apply Quicksort to the two sub-arrays.

    Sorting sub-array less than 28: [23, 11, 4]
    
    Pivot: 11
    Elements less than 11: [4]
    Pivot: 23
    Elements greater than 23: []
    Concatenate: [4, 11, 23]
    Sorting sub-array greater than 28: [45, 89, 77, 98]
    
    Pivot: 77
    Elements less than 77: [45]
    Pivot: 89
    Elements greater than 89: [98]
    Concatenate: [45, 77, 89, 98]
    
Step 4: Concatenate the sorted sub-arrays and the pivot element: [4, 11, 23, 28, 45, 77, 89, 98]

Final Sorted Array: [4, 11, 23, 28, 45, 77, 89, 98]

# Code
```cpp
#include<iostream>
using namespace std;

int QuickSort(int *arr, int st, int end) {
    int p = arr[end];
    int l = st - 1;
    for(int i = st; i < end; i++) {
        if(arr[i] < p) {
            l++;
            swap(arr[l], arr[i]);
        }
    }
    swap(arr[l + 1], arr[end]);
    return l + 1;
}

void sort(int *arr, int l, int r) {
    if(l < r) {
        int p = QuickSort(arr, l, r);
        sort(arr, l, p - 1);
        sort(arr, p + 1, r);
    }
}

int main() {
    int n; cin >> n;
    int *arr = new int[n];
    for(int i = 0; i < n; i++) cin >> arr[i];
    sort(arr, 0, n - 1);
    for(int i = 0; i < n; i++) cout << arr[i] << " ";
    delete[] arr;
}
```

# Time Complexity
Quicksort has an average-case time complexity of O(n log n), which makes it one of the fastest sorting algorithms. The algorithm divides the array into smaller sub-arrays based on a pivot element and recursively sorts them. However, in the worst-case scenario (when the pivot selection is not optimal), the time complexity can degrade to O(n^2), but this can be mitigated with better pivot selection strategies.

# Space Complexity
Quicksort has a space complexity of O(log n) due to the recursive nature of the algorithm. This is because each recursive call creates a new stack frame, which occupies memory proportional to the logarithm of the input size. In the best-case scenario, where the pivot choice evenly divides the array, the space complexity can be better than other algorithms like Merge Sort.

# Stability
Quicksort is not inherently stable. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. In Quicksort, the pivot selection and swapping operations can lead to the reordering of equal elements. However, it's possible to implement a stable version of Quicksort by carefully managing the swapping operations and pivot selection.

# Summary
Time Complexity: O(n log n) average-case, O(n^2) worst-case

Space Complexity: O(log n)

Stability: Not stable (can be made stable with extra effort in implementation)
