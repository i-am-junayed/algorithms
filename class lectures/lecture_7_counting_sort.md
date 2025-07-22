# Counting Sort: Time and Space Complexity Analysis

## Introduction

Counting Sort is a non-comparison-based sorting algorithm that sorts elements by counting the number of occurrences of each unique value. It is particularly efficient for sorting integers within a known range.

This documentation covers:

- Understanding the Counting Sort approach
- Step-by-step sorting process
- Time and Space Complexity analysis

---

## Counting Sort Algorithm

Counting Sort works as follows:

1. Find the maximum element in the array.
2. Create a counting array to store the frequency of each element.
3. Compute the cumulative sum of the count array.
4. Place elements in their correct position in the output array based on the count array.

---

## Example

For the array `[4, 2, 2, 8, 3, 3, 1]`, the sorting process is:

1. Find max element: `8`
2. Count occurrences: `[0, 1, 2, 2, 1, 0, 0, 0, 1]`
3. Compute cumulative count: `[0, 1, 3, 5, 6, 6, 6, 6, 7]`
4. Construct sorted array: `[1, 2, 2, 3, 3, 4, 8]`

---

## Implementation

```python
def counting_sort(arr):
    if not arr:
        return arr
    
    max_val = max(arr)
    count = [0] * (max_val + 1)
    output = [0] * len(arr)
    
    # Count occurrences
    for num in arr:
        count[num] += 1
    
    # Compute cumulative count
    for i in range(1, len(count)):
        count[i] += count[i - 1]
    
    # Build the output array
    for num in reversed(arr):
        output[count[num] - 1] = num
        count[num] -= 1
    
    return output
arr = [4, 2, 2, 8, 3, 3, 1]
print("Before Sorting:", arr)
sorted_arr = counting_sort(arr)
print("After Sorting:", sorted_arr)

Before Sorting: [4, 2, 2, 8, 3, 3, 1]
After Sorting: [1, 2, 2, 3, 3, 4, 8]

```
---
## Time Complexity Analysis

Counting Sort has a time complexity of **O(n + k)** in all cases, where **n** is the number of elements in the input array and **k** is the range of the input (the difference between the maximum and minimum values).

| Case | Time Complexity | Explanation |
|------|------------------|-------------|
| **Best Case** | O(n + k) | The algorithm always performs the same steps regardless of the input order. |
| **Worst Case** | O(n + k) | Even if the input is in reverse order or random, the steps remain the same. |
| **Average Case** | O(n + k) | The time complexity is linear and depends on the size of the input and the range of values. |

---

### Explanation of Counting Sort Time Complexity:
- **O(n)**: Counting the frequency of each element in the input array.
- **O(k)**: Building the sorted output array by iterating over the range of values.
- The overall time complexity is **O(n + k)** because both steps are necessary.

## Space Complexity Analysis

Counting Sort has a space complexity of **O(n + k)** because:

- It requires an auxiliary count array of size **k + 1**.
- An output array of size **n** is used to store the sorted elements.

---
## Summary

✅ **Efficient for sorting small integers with a limited range.**  
✅ **Stable sorting algorithm.**  
✅ **Best suited for scenarios where the range of numbers (k) is not excessively large compared to n.**  

❌ **Not suitable for sorting large datasets with widely varying numbers due to high space complexity.**  
❌ **Cannot sort floating-point numbers because it relies on integer indices.**  
✅ **Faster than comparison-based sorts for constrained input ranges but inefficient for general sorting tasks.**
