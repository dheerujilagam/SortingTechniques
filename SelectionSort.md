# Selection Sort

 Selection Sort is a simple sorting algorithm that repeatedly selects the minimum (or maximum) element from an unsorted portion of the array and moves it to the beginning (or end) of the sorted portion. 

# Algorithm

1. Iterate through the unsorted portion of the array.
2. For each iteration, find the index of the minimum element in the unsorted portion.
3. Swap the minimum element with the first element in the unsorted portion.

# Example
Let's consider an example with the input array [4, 2, 2, 1, 3]:

1. Initial Array: [4, 2, 2, 1, 3]
    * Minimum element: 1 (at index 3)
    * Swap elements at index 0 and 3: [1, 2, 2, 4, 3]

2. After 1st Iteration: [1, 2, 2, 4, 3]
    * Minimum element: 2 (at index 1)
    * Elements are equal, so no swap needed.

3. After 2nd Iteration: [1, 2, 2, 4, 3]
    * Minimum element: 2 (at index 2)
    * Elements are equal, so no swap needed.

5. After 3rd Iteration: [1, 2, 2, 4, 3]
   * Minimum element: 3 (at index 4)
   * Swap elements at index 2 and 4: [1, 2, 3, 4, 2]

6. After 4th Iteration: [1, 2, 3, 4, 2]
   * Minimum element: 4 (at index 3)
   * Swap elements at index 3 and 4: [1, 2, 3, 2, 4]

Final Sorted Array: [1, 2, 2, 3, 4]

# Iterative Code

```cpp
#include<iostream>
using namespace std;

void sort(int *arr, int n) {
	int i, j, ind;
	for(int i = 0; i < n; i++) {
		ind = i;
		for(int j = i + 1; j < n; j++) {
			if(arr[j] < arr[ind]) ind = j;
		}
		swap(arr[i], arr[ind]);
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

# Recursive Code

```cpp
#include<iostream>
using namespace std;

int minElement(int *arr, int i, int j) {
	if(i == j) return i;
	int k = minElement(arr, i + 1, j);
	return arr[i] < arr[k] ? i : k;
}

void sort(int *arr, int n, int index) {
	if(index == n) return ;
	int minIndex = minElement(arr, index, n - 1);
	if(minIndex != index) swap(arr[index], arr[minIndex]);
	sort(arr, n, index + 1);
}

int main(){
	int n; cin >> n;
	int *arr = new int[n];
	for(int i = 0; i < n; i++) cin >> arr[i];
	sort(arr, n, 0);
	for(int i = 0; i < n; i++) cout << arr[i] << " ";
	delete[] arr;
}
```
# Time Complexity
Selection Sort has a time complexity of O(n^2), where 'n' is the number of elements in the array. It involves iterating through the array multiple times, finding the minimum (or maximum) element each time and swapping it with the appropriate position. This makes the algorithm slower for larger arrays, as the number of comparisons and swaps grows quadratically with the size of the input.

# Space Complexity 
Selection Sort has a space complexity of O(1), which is constant space. The algorithm doesn't require any extra memory that scales with the input size. It performs all its operations using a few temporary variables, making it memory-efficient.

# Stability 
Selection Sort is not stable by default. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. In Selection Sort, during the swapping step, there's no guarantee that elements with the same value will maintain their original order. For example, if you have two equal elements, one before the other, and both need to be swapped to their correct positions, their relative order might change.

# Summary

Time Complexity

	Worst-case: O(n^2)
	
	Average-case: O(n^2)
	
	Best-case: O(n)

Space Complexity: O(1)

Stability: Stable
