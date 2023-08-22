# Insertion Sort

Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It is an "in-place" sorting algorithm, meaning it doesn't require extra memory to perform sorting operations. Insertion Sort is particularly efficient for small datasets or when the array is already partially sorted.

# Algorithm
1. Start with the second element (index 1) and consider it as the "key".
2. Compare the key with the elements before it in the sorted portion.
3. If the key is smaller (for ascending order) than the compared element, move the compared element one position ahead to make space for the key.
4. Repeat step 3 until you find an element that is smaller than the key, then insert the key in that position.
5. Move to the next unsorted element and repeat steps 2-4 until the entire array is sorted.

# Example
Let's work through the example with the input array [12, 11, 13, 5, 6]:

Initial Array: [12, 11, 13, 5, 6]

Step 1: Start with the second element (11) as the key.

Step 2: Compare the key (11) with the element before it (12). Since 11 < 12, move 12 one position ahead.

Array after moving 12: [12, 12, 13, 5, 6]

Step 3: Compare the key (11) with the element before it (12). 11 is smaller than 12, so insert the key at this position.

Array after insertion: [11, 12, 13, 5, 6]

Step 4: Move to the next unsorted element (13) and repeat the process.

Step 5: Move to the next unsorted element (5) and repeat the process.

Insert 5 in its correct position: [5, 11, 12, 13, 6]

Move to the next unsorted element (6) and repeat the process.

Insert 6 in its correct position: [5, 6, 11, 12, 13]

Final Sorted Array: [5, 6, 11, 12, 13]

```cpp
#include<iostream>
using namespace std;

void sort(int *arr, int n) {
	int i, j, key;
	for(i = 1; i < n; i++) {
		key = arr[i];
		j = i - 1;
		while(j >= 0 && arr[j] > key) {
			arr[j + 1] = arr[j];
			j--;
		}
		arr[j + 1] = key;
	}
}

int main() {
	int n; cin >> n;
	int *arr = new int[n];
	for(int i = 0; i < n; i++) cin >> arr[i];
	sort(arr, n);
	for(int i = 0; i < n; i++) cout << arr[i] << " ";
	delete[] arr;
}
```

# Time Complexity
Insertion Sort has a time complexity of O(n^2), where 'n' is the number of elements in the array. It involves comparing and shifting elements within the sorted portion for each unsorted element. This results in a quadratic number of operations, making it less efficient for larger arrays.

# Space Complexity
Insertion Sort has a space complexity of O(1), which means it uses a constant amount of additional memory regardless of the input size. It performs all sorting operations directly on the input array without requiring significant extra memory.

# Stability
Insertion Sort is stable by default. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. In Insertion Sort, when you're inserting an element into its correct position within the sorted portion, equal elements will maintain their original order.

# Summary

Time Complexity :

Worst-case: O(n^2)

Average-case: O(n^2)

Best-case: O(n^2)
  
Space Complexity: O(1)

Stability: Not Stable
