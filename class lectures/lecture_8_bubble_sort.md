# Bubble Sort: Time and Space Complexity Analysis

## Introduction
Bubble Sort is a comparison-based sorting algorithm that repeatedly swaps adjacent elements if they are in the wrong order. This process continues until the array is sorted.

This documentation covers:
- Understanding the Bubble Sort approach
- Step-by-step sorting process
- Time and Space Complexity analysis
- Bubble Sort Algorithm

Bubble Sort works as follows:
- Compare adjacent elements in the array.
- Swap them if they are in the wrong order.
- Repeat this process for each element until no swaps are needed.
Example:
For the array **[5, 3, 8, 4, 2]**, the sorting process is:
    - Pass 1: *[3, 5, 4, 2, 8]*
    - Pass 2: *[3, 4, 2, 5, 8]*
    - Pass 3: *[3, 2, 4, 5, 8]*
    - Pass 4: *[2, 3, 4, 5, 8]* (Sorted)

The largest element moves to its correct position in each pass, like bubbles rising to the surface.

## Implementation
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        swapped = False
        for j in range(n - 1 - i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break  # Optimization: Stop if already sorted

# Example
arr = [5, 3, 8, 4, 2]
print("Before Sorting:", arr)
bubble_sort(arr)
print("After Sorting:", arr)
```
---

## Time Complexity Analysis
Bubble Sort has a time complexity of **O(n²) in the worst and average case**s, but it can be optimized to **O(n)** in the best case.

| Case | Time Complexity | Explanation |
|------|---------------|-------------|
| **Best Case** | O(n) | If the array is already sorted, only one pass is needed.|
| **Worst Case** | O(n²) | If the array is sorted in reverse order, maximum swaps are required. |
| **Average Case** | O(n²) | On average, each element is compared and swapped multiple times. |

---
## Space Complexity Analysis
Bubble Sort has a **space complexity of O(1)** because:
- Bubble Sort is an in-place sorting algorithm and requires O(1) auxiliary space, meaning it does not use extra memory apart from the input array.
---

## Summary
- **Bubble Sort is simple but inefficient for large datasets due to O(n²) complexity.**
- **Best suited for small lists or nearly sorted data (O(n) in best case).**
- **It is an in-place and stable sorting algorithm.**
- **When swapping is more affordable than shifting, Bubble Sort may be preferred over Insertion Sort.** 
- **Not recommended for real-world applications; better alternatives include Insertion Sort, Quick Sort, or Merge Sort.**
