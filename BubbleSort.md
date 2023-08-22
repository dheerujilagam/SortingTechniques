# Bubble Sort

Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The process is repeated for each element until the entire list is sorted.

Let's say we have an unsorted array: [5, 3, 8, 1, 2]

Pass 1:

Compare 5 and 3, swap them (array: [3, 5, 8, 1, 2])

Compare 5 and 8, no swap

Compare 8 and 1, swap them (array: [3, 5, 1, 8, 2])

Compare 8 and 2, swap them (array: [3, 5, 1, 2, 8])

Pass 2:

Compare 3 and 5, no swap

Compare 5 and 1, swap them (array: [3, 1, 5, 2, 8])

Compare 5 and 2, swap them (array: [3, 1, 2, 5, 8])

Compare 5 and 8, no swap

Pass 3:

Compare 3 and 1, swap them (array: [1, 3, 2, 5, 8])

Compare 3 and 2, swap them (array: [1, 2, 3, 5, 8])

Compare 5 and 8, no swap

Pass 4:

Compare 1 and 2, no swap

Compare 2 and 3, no swap

Compare 3 and 5, no swap

Compare 5 and 8, no swap

No swaps occurred in the last pass, which means the array is sorted.

Final sorted array: [1, 2, 3, 5, 8]

# Iterative Code

```cpp
#include<iostream>
using namespace std;

void sort(int *arr, int n) {
	int i, j, flag;
	for(int i = 0; i < n - 1; i++) {
		flag = 0;
		for(int j = 0; j < n - i - 1; j++) {
			if(arr[j] > arr[j + 1]) {
				swap(arr[j], arr[j + 1]);
				flag = 1;
			}
		}
		// for(int k = 0; k < n; k++) cout << arr[k] << " ";
		// cout << endl;
		if(flag == 0) break;
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

void sort(int *arr, int n) {
	if(n == 1) return;
	int count = 0;
	for(int i = 0; i < n - 1; i++) {
		if(arr[i] > arr[i + 1]) {
			swap(arr[i], arr[i + 1]);
			count++;
		}
	}
	if(count == 0) return ;
	sort(arr, n - 1);
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

# Input 
```
7
15 1 13 2 6 3 19
```

# Output
```
1 2 3 6 13 15 19
```

# Time Complexity:
Bubble Sort has a worst-case and average-case time complexity of O(n^2), where "n" is the number of elements in the array. This is because, in the worst case, the algorithm needs to perform n-1 comparisons for the first pass, n-2 comparisons for the second pass, and so on, until the last two elements are compared. The total number of comparisons is roughly (n-1) + (n-2) + ... + 1, which is approximately (n^2)/2. The best-case time complexity of Bubble Sort is O(n) when the array is already sorted. However, even in the best-case scenario, the algorithm will still perform n-1 passes, leading to an average-case time complexity of O(n^2) due to the number of comparisons and swaps.

# Space Complexity:
Bubble Sort is an in-place sorting algorithm, meaning it doesn't require additional memory space proportional to the input size. The space complexity of Bubble Sort is O(1), as it only requires a constant amount of extra space to store temporary variables used in the swapping process.

# Stability:
Bubble Sort is a stable sorting algorithm. Stability in sorting means that the relative order of equal elements remains unchanged after sorting. In Bubble Sort, whenever two adjacent elements are swapped, they change their positions. However, if two elements are equal and they are adjacent, the swapping will not occur. This ensures that the relative order of equal elements is preserved in the sorted array.

# In summary:

Time Complexity: O(n^2) (worst-case and average-case), O(n) (best-case)

Space Complexity: O(1)

Stability: Stable
