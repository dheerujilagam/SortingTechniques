# Counting Sort
Counting Sort is a non-comparative integer sorting algorithm that works well when the range of input values is small compared to the number of elements. It works by counting the occurrences of each element and then using that information to place the elements in their correct sorted positions.

# Algorithm
1. Find the range of input values (minimum and maximum).
2. Initialize an auxiliary array to store the count of each unique element.
3. Count the occurrences of each element in the input array.
4. Modify the auxiliary array to store the cumulative count of elements.
5. Iterate through the original input array in reverse and place each element in its correct sorted position using the cumulative count from the auxiliary array.
6. Decrement the cumulative count for the placed element.

# Example
Let's work through an example using the input array [4, 2, 2, 8, 3, 3, 1].

Step 1: Find the range of input values (1 to 8).

Step 2: Initialize an auxiliary array of size 8 (range + 1) to store the count of each element.

Auxiliary array: [0, 0, 0, 0, 0, 0, 0, 0, 0]

Step 3: Count the occurrences of each element.

Auxiliary array after counting: [1, 2, 2, 2, 0, 0, 0, 1, 0]

Step 4: Modify the auxiliary array to store cumulative counts.

Auxiliary array after cumulative counting: [1, 3, 5, 7, 7, 7, 7, 8, 8]

Step 5: Iterate through the original array and place elements in their correct positions.

Sorted array: [1, 2, 2, 3, 3, 4, 8]

Final Sorted Array: [1, 2, 2, 3, 3, 4, 8]

# Code
```cpp
#include<iostream>
using namespace std;

int getMax(int *arr, int n) {
	int maxValue = arr[0];
	for(int i = 1; i < n; i++) maxValue = (arr[i] > maxValue) ? arr[i] : maxValue;
		return maxValue;
}

void sort(int *arr, int n) {
	int maxValue = getMax(arr, n);
	int count[maxValue + 1] = {0};
	int sortedArr[n];
	for(int i = 0; i < n; i++) count[arr[i]]++;
	for(int i = 1; i <= maxValue; i++) count[i] += count[i - 1];
	for(int i = n - 1; i >= 0; i--) {
		sortedArr[count[arr[i]] - 1] = arr[i];
		count[arr[i]]--;
	}
	for(int i = 0; i < n; i++) arr[i] = sortedArr[i];
}	

int main() {
	int n; cin >> n;
	int *arr = new int[n];
	for(int i = 0; i < n; i++) cin >> arr[i];
	sort(arr, n);
	for(int i = 0; i < n; i++) cout << arr[i] << " ";
	delete arr[];
}
```

# Time Complexity
Counting Sort has a time complexity of O(n + k), where 'n' is the number of elements in the array and 'k' is the range of input values. It efficiently sorts elements when the range of values is small compared to the number of elements. However, its performance degrades when the range becomes significantly larger.

# Space Complexity
Counting Sort has a space complexity of O(n + k), where 'n' is the number of elements and 'k' is the range of input values. It requires additional space for the auxiliary array used to count the occurrences of each element. The space complexity can be higher than other sorting algorithms for larger ranges.

# Stability
Counting Sort is inherently stable. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. In Counting Sort, equal elements are sorted in the same order as they appear in the input array, maintaining stability.

# Summary
Time Complexity: O(n + k)

Space Complexity: O(n + k)

Stability: Stable
