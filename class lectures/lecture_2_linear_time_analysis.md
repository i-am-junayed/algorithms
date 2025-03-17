# Linear Time Analysis Using Time and Step Counter

## Introduction

This document analyzes the **linear time complexity** of summing a list using two different approaches:
1. **Time Measurement** – Measuring the execution time.
2. **Step Counter** – Counting the number of computational steps.

By analyzing both, we can understand how execution time and step count grow as the input size increases.

---

## 1. Time-Based Analysis

This method measures the execution time of the function using the `time` module.

### Code:

```python
import time

def sum_list(lst):
    total = 0
    for i in lst:
        total += i
    return total

lst = [5, 4, 8, 2, 10, 5, 4, 8, 2, 10, 5, 4, 8, 2, 10]

start_time = time.time()
result = sum_list(lst)
end_time = time.time()

total_time = end_time - start_time

print("Execution Time:", total_time)
print("Sum:", result)
```

### Time Complexity:
- **O(n)** since the function iterates through the entire list once.

### Observations:
- The execution time depends on system performance and external factors (e.g., CPU load).
- Time measurement varies slightly in each run.

---

## 2. Step Counter-Based Analysis

This method explicitly counts the number of computational steps.

### Code:

```python
def sum_list(lst):
    total = 0
    step = 1  # Initializing step counter
    
    for i in lst:
        step += 1  # Iteration step
        total += i
    
    step += 1  # Final return step
    return total, step

lst = [5, 4, 8, 2, 10, 5, 4, 8, 2, 10, 5, 4, 8, 2, 10]

result, steps = sum_list(lst)

print("Sum:", result)
print("Total Steps:", steps)
```

### Step Complexity:
- **O(n)** since the function performs a constant number of operations per element.
- Steps can be explicitly counted and verified.

### Observations:
- Step count grows proportionally with `n`.
- Unlike execution time, step count remains consistent across different runs and machines.

---

## Comparison and Conclusion

| Approach | Complexity | Stability |
|----------|------------|------------|
| Time-Based | O(n) | Varies due to system conditions |
| Step Counter | O(n) | Consistent in every execution |

### Key Takeaways:
- **Step analysis is a more reliable way to understand algorithm efficiency** because it is independent of hardware variations.
- **Time measurement is useful for real-world performance testing** but is influenced by external factors.
- **Both approaches confirm that summing a list runs in O(n) time complexity.**
