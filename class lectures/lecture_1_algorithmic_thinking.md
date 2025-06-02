# Prime Number Check: Optimized vs Naive Approach

## Introduction

This repository demonstrates how algorithmic thinking can transform naive solutions into efficient ones. We explore two classic problems:

**Prime Number Checking**
- Naive O(n) approach vs optimized O(√n) solution
- How mathematical insight leads to better performance
  
**Duplicate Detection**
- Brute force O(n²) nested loops
- Optimized O(n) solution using hash sets
- The power of choosing proper data structures

Through these examples, you'll learn:
- How to analyze time complexity
- When to trade space for speed
- Techniques for optimizing algorithms
- Why theoretical foundations matter in practice
  
Each solution includes:
- Working Python implementations
- Time/space complexity analysis
- Performance comparisons
- Clear guidelines for when to use each approach
    
## Naive Approach (Inefficient)

The naive approach checks all numbers from `2` to `num-1`, making it inefficient for large numbers.

### Code:

```python
def is_prime(num):
    if num <= 1:
        return False
    else:
        for i in range(2, num, 1):
            print(i)  # Debugging output
            if num % i == 0:
                return False
    return True

print(is_prime(int(input("Enter a number: "))))
```

### Time Complexity:

- **O(n)** in the worst case.
- This method iterates through all numbers up to `num-1`, making it very slow for large inputs.

## Optimized Approach (Efficient)

A more efficient method reduces the number of iterations by only checking divisibility up to `sqrt(num)`. This is because if a number `n` is divisible by some number `p`, then `p` must be less than or equal to `sqrt(n)`, otherwise, there would be a smaller factor that we would have already checked.

### Code:

```python
def is_prime(num):
    if num <= 1:
        return False
    else:
        for i in range(2, int(num**0.5) + 1, 1):
            print(i)  # Debugging output
            if num % i == 0:
                return False
    return True

print(is_prime(int(input("Enter a number: "))))
```

### Time Complexity:

- **O(√n)** in the worst case.
- This method significantly reduces the number of iterations, making it much faster for large numbers.

## Comparison

| Approach          | Time Complexity | Efficiency           |
|------------------|---------------|---------------------|
| Naive Approach  | O(n)          | Slow for large numbers |
| Optimized Approach | O(√n)       | Much faster        |


# Duplicate Detection Algorithms: Brute Force vs Optimized Approaches

## Table of Contents
- [Brute Force Approach (O(n²))](#brute-force-approach-on²)
- [Optimized List Approach (O(n²))](#optimized-list-approach-on²)
- [Optimized Set Approach (O(n))](#optimized-set-approach-on)
- [Performance Comparison](#performance-comparison)
- [Why the Time Complexity Differences?](#why-the-time-complexity-differences)
- [When to Use Each Approach](#when-to-use-each-approach)

---

## Brute Force Approach (O(n²))
Checks all possible pairs using nested loops.

### Code: 
```python
def find_duplicate_brute(lst, count=0):
    for i in range(len(lst)):
        for j in range(len(lst)):
            count += 1
            if i != j and lst[i] == lst[j]:
                return True, count
    return False, count
```
**Characteristics:**
- Double nested loops
- Counts all comparisons
- Returns at first duplicate found
- No extra memory usage (space complexity: O(1))

```python
lst = [3, 6, 2, 23, 9, 1, 29]
print(find_duplicate_brute(lst))  # (False, 49) for 7 elements (7×7 checks)
```
# Optimized List Approach (O(n²))
Uses a single loop but still O(n²) due to list searches.

### Code:
```python
def find_duplicate_list(lst, count=0):
    seen = []
    for item in lst:
        count += 1
        if item in seen:  # O(n) operation
            return True, count
        seen.append(item)
    return False, count
```
**Characteristics:**
- Single loop + linear search
- Tracks seen elements in a list
- Still O(n²) worst-case (but better average case than brute force)
- Space complexity: O(n)

# Optimized Set Approach (O(n))
Uses hash-based set for O(1) lookups.

### Code:

```python
def find_duplicate_set(lst, count=0):
    seen = set()
    for item in lst:
        count += 1
        if item in seen:  # O(1) operation
            return True, count
        seen.add(item)
    return False, count
```
**Characteristics:**
- Single loop with O(1) lookups
- Uses hash table implementation
- True O(n) time complexity
- Space complexity: O(n)
  
## Performance Comparison

| Approach          | Time Complexity | Efficiency           |
|------------------|----------------|----------------------|
| Brute Force      | O(n²)          | Extremely slow for large lists |
| Optimized List   | O(n²)          | Better than brute force but still slow |
| Optimized Set    | O(n)           | Fast for all list sizes |

**Key Takeaways:**
- The brute force method becomes impractical for lists with >100 elements
- Even the optimized list approach doesn't scale well due to O(n²) complexity
- The set-based solution maintains excellent performance even for millions of items

# Why the Time Complexity Differences?
**List Lookups are O(n)**
```python
if x in my_list:  # Requires scanning entire list
```
Checks elements one-by-one

*Worst case: scans all n elements for each of n items → O(n²)*

**Set Lookups are O(1)**
```python
if x in my_set:  # Uses hash table lookup
```
Computes hash value to find bucket

*Average case: direct access to element*

## When to Use Each Approach

**Brute Force (O(n²))**
- Only for tiny lists (≤5 elements)
- When memory is extremely constrained

**Optimized List (O(n²))**
- Small lists (<100 items)
- When you can't use sets (rare)

**Optimized Set (O(n))**
- Default choice for all cases
- Especially critical for large datasets

## Conclusion

**For prime checking:**
Always use the square root method - it's dramatically faster for large numbers while being just as easy to implement as the naive approach.

**For duplicate detection:**
The set-based solution wins every time. While the brute force and list methods help understand the problem, they're impractical for real-world use.

**Golden rule:**
- Always analyze your problem before coding
- Look for mathematical insights
- Choose data structures wisely
- Test with edge cases


Happy Coding! 🚀
