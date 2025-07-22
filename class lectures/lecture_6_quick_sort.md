# Quick Sort: Time and Space Complexity Analysis

## Introduction
Quick Sort is a **divide and conquer** sorting algorithm that partitions an array into subarrays around a pivot element, then recursively sorts the subarrays.

This documentation covers:
- **Understanding the Divide and Conquer approach**
- **Step-by-step partitioning process**
- **Time and Space Complexity analysis**

---

## Divide and Conquer Approach
Quick Sort also follows a **Divide and Conquer** paradigm:

1. **Divide**: Select a pivot and partition the array so that all elements less than the pivot come before it, and all elements greater come after it.  
2. **Conquer**: Recursively apply the same strategy to the left and right subarrays.  
3. **Combine**: Since the array is sorted in place, no additional merging is needed.

**Example**:

For the array `[38, 27, 43, 3, 9, 82, 10]`, choosing the last element as pivot, the partitioning might go like this:

Pivot = 10
[3, 9] + [10] + [38, 27, 43, 82] → [3, 9, 10, 38, 27, 43, 82]

Next, recursively apply Quick Sort to:
[3, 9] and [38, 27, 43, 82]

Partitioning continues until subarrays of size 1 are reached.  
Unlike Merge Sort, Quick Sort doesn't need to merge; the elements are sorted in place during partitioning.

---

## Implementation

```python
def quickSort(arr, low, high):
    if low < high:
        # Partition the array and get the pivot index
        pivot_index = partition(arr, low, high)

        # Recursively sort elements before and after partition
        quickSort(arr, low, pivot_index - 1)
        quickSort(arr, pivot_index + 1, high)

def partition(arr, low, high):
    pivot = arr[high]  # Choose the last element as pivot
    i = low - 1  # Index of smaller element

    for j in range(low, high):
        if arr[j] <= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]  # Swap

    arr[i + 1], arr[high] = arr[high], arr[i + 1]  # Place pivot correctly
    return i + 1  # Return pivot index

# Example
arr = [38, 27, 43, 3, 9, 82, 10]
print("Before Sorting:", arr)
quickSort(arr, 0, len(arr) - 1)
print("After Sorting:", arr)

```

## Time Complexity Analysis

Quick Sort has a **best-case and average-case time complexity of O(n log n)**, but a **worst-case of O(n²)** when the pivot selection is poor (e.g., always the smallest or largest element).

| Case         | Time Complexity | Explanation                                      |
|--------------|------------------|--------------------------------------------------|
| **Best Case**   | O(n log n)       | Pivot divides array into two equal halves.       |
| **Worst Case**  | O(n²)            | Pivot is always the smallest or largest element. |
| **Average Case**| O(n log n)       | Balanced partitions on average over multiple calls. |

---

## Space Complexity Analysis

Quick Sort has a **space complexity of O(log n)** on average due to:

- Recursive calls in the call stack (not due to additional arrays).
- It is **in-place**, so no extra arrays are created during sorting.

However, in the **worst case** (unbalanced partitions), space complexity can go up to **O(n)** due to deep recursion.

---

## Summary

- **Quick Sort is efficient with average-case O(n log n) time complexity.**
- **Performs sorting in place, requiring only O(log n) auxiliary space.**
- **Can degrade to O(n²) time with poor pivot selection.**
- **Follows the Divide and Conquer paradigm but uses partitioning instead of merging.**
- **Often faster in practice than Merge Sort due to better cache performance and no extra memory usage.**
