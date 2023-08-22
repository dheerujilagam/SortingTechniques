# Merge Sort
Merge Sort is a divide-and-conquer sorting algorithm that works by recursively dividing the unsorted array into smaller subarrays until each subarray contains a single element. It then merges these subarrays back together in a sorted manner. Merge Sort is known for its consistent time complexity and is often used for sorting large datasets.

# Algorithm
    1. Divide the unsorted array into two halves.
    2. Recursively sort each of the two halves.
    3. Merge the sorted halves to create a single sorted array.
   
# Example
Let's work through an example using the input array [38, 27, 43, 3, 9, 82, 10].

Step 1: Divide the array into two halves: [38, 27, 43, 3] and [9, 82, 10].

Step 2: Recursively sort each half.

    Left half: [38, 27, 43, 3]
    
    Divide into [38, 27] and [43, 3]
    Recursively sort left half: [27, 38]
    Recursively sort right half: [3, 43]
    Merge sorted halves: [3, 27, 38, 43]
    
    Right half: [9, 82, 10]
    
    Divide into [9] and [82, 10]
    Recursively sort right half: [10, 82]
    Merge sorted halves: [9, 10, 82]

Step 3: Merge the two sorted halves: [3, 9, 10, 27, 38, 43, 82]

Final Sorted Array: [3, 9, 10, 27, 38, 43, 82]

# Code

```cpp
#include<iostream>
using namespace std;

void merge(int *arr, int l, int m, int r) {
	int n1 = m - l + 1, n2 = r - m;
	int *a1 = new int[n1], *a2 = new int[n2];
	for(int i = 0; i < n1; i++) a1[i] = arr[l + i];
	for(int i = 0; i < n2; i++) a2[i] = arr[m + i + 1];
	int i = 0, j = 0, k = l;
	while(i < n1 && j < n2) {
		if(a1[i] <= a2[j]) {
			arr[k] = a1[i++];
		} else {
			arr[k] = a2[j++];
		}
		k++;
	}
	while(i < n1) {
		arr[k++] = a1[i++];
	}
	while(j < n2) {
		arr[k++] = a2[j++];
	}
	delete[] a1;
	delete[] a2;
}
 
void mergeSort(int *arr, int l, int r) {
	if(l >= r) return ;
	int m = (l + r) / 2;
	mergeSort(arr, l, m);
	mergeSort(arr, m + 1, r);
	merge(arr, l, m, r);
}

int main() {
	int n; cin >> n;
	int *arr = new int[n];
	for(int i = 0; i < n; i++) cin >> arr[i];
	mergeSort(arr, 0, n - 1);
	for(int i = 0; i < n; i++) cout << arr[i] << " ";
	delete[] arr;
}
```

# Time Complexity
Merge Sort has a consistent time complexity of O(n log n), where 'n' is the number of elements in the array. It divides the array into smaller subarrays and then merges them back together in a sorted manner. The merge step takes O(n) time, and the division step occurs recursively, leading to a balanced and efficient runtime for sorting.

# Space Complexity
Merge Sort has a space complexity of O(n), which means it requires additional memory proportional to the size of the input array. This is because it needs to create temporary arrays during the merging process. However, Merge Sort can be adapted to use an in-place merge to reduce the space complexity to O(1) at the cost of increased time complexity.

# Stability
Merge Sort is stable by nature. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. Since Merge Sort compares elements and merges them in a specific order, equal elements will maintain their original order, making it a stable sorting algorithm.

# Summary
Time Complexity: O(n log n)

Space Complexity: O(n)

Stability: Stable
