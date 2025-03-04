# Insertion Sort: Time Complexity Analysis

## Introduction
Insertion sort is a simple yet inefficient sorting algorithm with a **time complexity of O(n²)** in the worst and average cases. This document analyzes its performance using two different approaches:
1. **Time Measurement** – Measuring the execution time.
2. **Step Counter** – Counting the number of computational steps.

We also evaluate the **best, worst, and average cases** for insertion sort.

---

## 1. Time-Based Analysis

This method measures the execution time of the insertion sort algorithm using the `time` module.

### Code:

```python
import time

def insertion_sort(arr):
    for i in range(1, len(arr)):
        temp = arr[i]
        j = i - 1
        while j >= 0 and temp < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = temp
    return arr

arr = [21, 11, 1, 25, 46, 34, 21, 6, 2, 98, 21, 11, 1, 25, 46, 17, 25, 46, 34, 21, 6]

start_time = time.time()
sorted_arr = insertion_sort(arr.copy())
end_time = time.time()

total_time = end_time - start_time

print("Execution Time:", total_time)
print("Sorted Array:", sorted_arr)
```

### Observations:
- The execution time grows quadratically as the list size increases.
- Time varies due to system conditions and CPU performance.

---

## 2. Step Counter-Based Analysis

This method explicitly counts the number of computational steps.

### Code:

```python
def insertion_sort(arr):
    step_counter = 0

    step_counter += 1  # Initial step
    for i in range(1, len(arr)):
        temp = arr[i]
        j = i - 1

        step_counter += 1  # Outer loop step
        while j >= 0 and temp < arr[j]:
            step_counter += 1  # Comparison step
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = temp
        step_counter += 1  # Assignment step

    step_counter += 1  # Final step
    return arr, step_counter

arr = [21, 11, 1, 25, 46, 34, 21, 6, 2, 98, 21, 11, 1, 25, 46, 17, 25, 46, 34, 21, 6]
sorted_arr, step_count = insertion_sort(arr.copy())
print("Total Steps:", step_count)
```

### Observations:
- The number of steps increases quadratically with the input size.
- Step count is independent of system performance and provides a consistent measure of complexity.

---

## Best, Worst, and Average Case Analysis

| Case | Input Condition | Time Complexity | Explanation |
|------|---------------|---------------|-------------|
| **Best Case** | Already sorted list | O(n) | The algorithm only checks each element once with no swaps. |
| **Worst Case** | Reversed list | O(n²) | Each element must be shifted in every iteration. |
| **Average Case** | Random order | O(n²) | The number of shifts and comparisons follows a quadratic growth pattern. |

### Key Takeaways:
- **Insertion sort is inefficient for large datasets due to its O(n²) complexity.**
- **Best case occurs when the array is already sorted, achieving O(n) complexity.**
- **In real-world applications, insertion sort is useful for small arrays or nearly sorted data.**
