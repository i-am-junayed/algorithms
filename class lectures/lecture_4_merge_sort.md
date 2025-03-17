# Merge Sort: Time and Space Complexity Analysis

## Introduction
Merge Sort is a **divide and conquer** sorting algorithm that recursively splits an array into smaller subarrays, sorts them, and then merges them back together in sorted order.

This documentation covers:
- **Understanding the Divide and Conquer approach**
- **Step-by-step merging process**
- **Time and Space Complexity analysis**

---

## Divide and Conquer Approach
Merge Sort follows a **Divide and Conquer** paradigm:
1. **Divide**: Split the array into two halves recursively until each half contains a single element.
2. **Conquer**: Sort each half recursively.
3. **Combine**: Merge the two sorted halves back together to get the final sorted array.

Example:

For the array `[38, 27, 43, 3, 9, 82, 10]`, the splitting occurs as follows:

```
[38, 27, 43, 3, 9, 82, 10]
=> [38, 27, 43, 3]  |  [9, 82, 10]
=> [38, 27] | [43, 3]  |  [9, 82] | [10]
=> [38] | [27] | [43] | [3]  |  [9] | [82] | [10]
```

Once the array is divided, merging begins:

```
[38] + [27] → [27, 38]
[43] + [3] → [3, 43]
[9] + [82] → [9, 82]
```

Then, the sorted halves merge:

```
[27, 38] + [3, 43] → [3, 27, 38, 43]
[9, 82] + [10] → [9, 10, 82]
```

Final merge:

```
[3, 27, 38, 43] + [9, 10, 82] → [3, 9, 10, 27, 38, 43, 82]
```

---

## Implementation

```python
def mergeSort(arr, left, right):
    if left >= right:
        return  # Base case: single element is already sorted

    mid = (left + right) // 2  # Find the middle index

    # Recursively sort both halves
    mergeSort(arr, left, mid)
    mergeSort(arr, mid + 1, right)

    # Merge sorted halves
    merge(arr, left, mid, right)

def merge(arr, left, mid, right):
    temp = []  # Temporary list for merging
    i, j = left, mid + 1

    # Merge elements in sorted order
    while i <= mid and j <= right:
        if arr[i] < arr[j]:
            temp.append(arr[i])
            i += 1
        else:
            temp.append(arr[j])
            j += 1

    # Add remaining elements
    temp.extend(arr[i:mid + 1])
    temp.extend(arr[j:right + 1])

    # Copy back to original array
    arr[left:right + 1] = temp

# Example
arr = [38, 27, 43, 3, 9, 82, 10]
print("Before Sorting:", arr)
mergeSort(arr, 0, len(arr) - 1)
print("After Sorting:", arr)
```

---

## Time Complexity Analysis
Merge Sort has a **time complexity of O(n log n)** in all cases.

| Case | Time Complexity | Explanation |
|------|---------------|-------------|
| **Best Case** | O(n log n) | Recursively divides and merges efficiently. |
| **Worst Case** | O(n log n) | Every element needs merging and recursion is applied. |
| **Average Case** | O(n log n) | Similar to worst case since it always divides and merges. |

---

## Space Complexity Analysis
Merge Sort has a **space complexity of O(n)** because:
- It requires extra space to store temporary arrays for merging.
- Unlike in-place sorting algorithms, Merge Sort relies on additional memory for merging subarrays.

---

## Summary
- **Merge Sort is efficient for large datasets due to O(n log n) time complexity.**
- **Uses extra space for merging (O(n) space complexity).**
- **Preferred over O(n²) algorithms like Insertion Sort for large inputs.**
- **Follows the Divide and Conquer strategy for sorting.**
