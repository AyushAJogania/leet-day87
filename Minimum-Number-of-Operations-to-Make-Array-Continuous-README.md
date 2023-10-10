# leet-day87

# Minimum Operations to Make Array Continuous

You are given an integer array `nums`. The array is considered continuous if the following conditions are met:

1. All elements in `nums` are unique.
2. The difference between the maximum element and the minimum element in `nums` equals `nums.length - 1`.

Your task is to find the minimum number of operations required to make the array continuous. In one operation, you can replace any element in `nums` with any integer.

## Example

**Input:**

```
nums = [4, 2, 5, 3]
```

**Output:**

```
0
```

**Explanation:** The given array `nums` is already continuous.

**Input:**

```
nums = [1, 2, 3, 5, 6]
```

**Output:**

```
1
```

**Explanation:** One possible solution is to change the last element to `4`. The resulting array `[1, 2, 3, 5, 4]` is continuous.

**Input:**

```
nums = [1, 10, 100, 1000]
```

**Output:**

```
3
```

**Explanation:** One possible solution is to:
- Change the second element to `2`.
- Change the third element to `3`.
- Change the fourth element to `4`.
The resulting array `[1, 2, 3, 4]` is continuous.

## Constraints

- `1 <= nums.length <= 10^5`
- `1 <= nums[i] <= 10^9`

## Approach

To find the minimum number of operations, we can follow these steps:

1. Sort the `nums` array in ascending order.
2. Create a new vector `uniqueNums` to store the unique elements of `nums`.
3. Initialize `ans` to a large value (e.g., `INT_MAX`) to keep track of the minimum operations.
4. Iterate through each unique element `s` in `uniqueNums` and calculate the maximum possible end value `e` as `s + n - 1`, where `n` is the length of `nums`.
5. Use binary search (specifically `std::upper_bound`) to find the index of the smallest element in `uniqueNums` that is greater than `e`. This index represents the right end of the window.
6. Calculate the number of elements outside the window as `n - (idx - i)`, where `idx` is the index found in step 5, and `i` is the index of the current unique element `s`.
7. Update `ans` with the minimum value of `ans` and the number of elements outside the window.
8. Repeat steps 4 to 7 for all unique elements in `uniqueNums`.
9. Finally, return `ans` as the minimum number of operations.

The use of binary search (`std::upper_bound`) ensures that we efficiently find the right end of the window for each unique element, making the solution O(n log n) in time complexity.

