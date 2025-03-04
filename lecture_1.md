# Prime Number Check: Optimized vs Naive Approach

## Introduction

This repository demonstrates two different approaches to checking whether a number is prime. The first approach is a naive method, and the second one is an optimized method using the square root technique to improve efficiency.

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

## Conclusion

By applying the square root optimization, we significantly improve the performance of prime number detection, making it practical for larger inputs.

Happy Coding! 🚀
