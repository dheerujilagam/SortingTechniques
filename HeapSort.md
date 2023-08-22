# Heap Sort
Heap Sort is a comparison-based sorting algorithm that uses a binary heap data structure to build a heap and extract the maximum (or minimum) element iteratively to build the sorted array. It has an average and worst-case time complexity of O(n log n), making it efficient for larger datasets.

# Algorithm
1. Build a max-heap (for ascending order) or min-heap (for descending order) from the input array.
2. Continuously extract the root element (which is the maximum for max-heap or minimum for min-heap) and place it at the end of the array.
3. Reduce the heap size by one and re-heapify the remaining elements.
4. Repeat steps 2 and 3 until the entire array is sorted.

# Example
Let's work through an example using the input array [12, 11, 13, 5, 6, 7].

Step 1: Build a max-heap from the input array.

Initial max-heap: [13, 11, 12, 5, 6, 7]

Step 2: Continuously extract the root element (maximum) and place it at the end of the array.

Array after extraction: [7, 11, 12, 5, 6 | 13]

Step 3: Reduce the heap size and re-heapify.

Re-heapified max-heap: [12, 11, 7, 5, 6]

Step 2 (again): Extract the root element (maximum) and place it at the end.

Array after extraction: [6, 11, 7, 5 | 12]

Step 3 (again): Reduce the heap size and re-heapify.

Re-heapified max-heap: [11, 6, 7, 5]

Step 2 (once more): Extract the root element (maximum) and place it at the end.

Array after extraction: [5, 6, 7 | 11]

Step 3 (once more): Reduce the heap size and re-heapify.

Re-heapified max-heap: [7, 6, 5]

Step 2 (final time): Extract the root element (maximum) and place it at the end.

Array after extraction: [5, 6 | 7]

Final Sorted Array: [5, 6, 7, 11, 12, 13]

# Code
```cpp
#include<iostream>
using namespace std;

void heapify(int *arr, int n, int i) {
    int largest = i;
    int left = 2 * i + 1, right = 2 * i + 2;
    if(left < n && arr[left] > arr[largest]) largest = left;
    if(right < n && arr[right] > arr[largest]) largest = right;
    if(largest != i) {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(int *arr, int n) {
    for(int i = (n / 2) - 1; i >= 0; i--) heapify(arr, n, i);
    // for(int i = 0; i < n; i++) cout << arr[i] << " ";
    // cout << endl;
    for(int i = n - 1; i >= 0; i--) {
        swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}

int main() {
    int n; cin >> n;
    int *arr = new int[n];
    for(int i = 0; i < n; i++) cin >> arr[i];
    heapSort(arr, n);
    for(int i = 0; i < n; i++) cout << arr[i] << " ";
    delete[] arr;
}
```

# Time Complexity
Heap Sort has an average and worst-case time complexity of O(n log n), making it efficient for larger datasets. The process of building the heap takes O(n) time, and for each extraction of the root element and re-heapification, it takes O(log n) time. Thus, the overall time complexity is O(n log n).

# Space Complexity
Heap Sort has a space complexity of O(1) for its heap operations. While it does require additional memory for the heap data structure, the space used is constant and doesn't scale with the input size. The heap sort process is performed in-place on the input array.

# Stability
Heap Sort is not inherently stable. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. In Heap Sort, swapping elements during heapification may change the order of equal elements, leading to potential instability.

# Summary
Time Complexity: O(n log n)

Space Complexity: O(1)

Stability: Not stable
