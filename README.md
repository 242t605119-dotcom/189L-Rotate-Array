# LeetCode 189 - Rotate Array

## Problem

Given an integer array `nums`, rotate the array to the right by `k` steps.

Each rotation moves the last element to the beginning of the array.

The array should be modified in-place.

## Example

### Input

```text
nums = [1,2,3,4,5,6,7]
k = 3
```

### Output

```text
[5,6,7,1,2,3,4]
```

The array is rotated to the right 3 times.

## Approach

The simple idea is to divide the array into two parts:

```text
nums = [1,2,3,4,5,6,7]
```

For `k = 3`:

```text
Last 3 elements → [5,6,7]
Remaining elements → [1,2,3,4]
```

Place the last `k` elements at the beginning:

```text
[5,6,7] + [1,2,3,4]
```

Result:

```text
[5,6,7,1,2,3,4]
```

## Python Program

```python
class Solution:
    def rotate(self, nums, k):
        n = len(nums)
        k = k % n

        nums[:] = nums[-k:] + nums[:-k]
```

## Why Use `k % n`?

If `k` is greater than the length of the array, rotating the array `n` times brings it back to its original position.

For example:

```text
n = 5
k = 7
```

Instead of rotating 7 times:

```text
7 % 5 = 2
```

So we only need to rotate it by 2 positions.

## Example 2

### Input

```text
nums = [-1,-100,3,99]
k = 2
```

The last two elements are:

```text
[3,99]
```

The remaining elements are:

```text
[-1,-100]
```

After rotation:

```text
[3,99,-1,-100]
```

### Output

```text
[3,99,-1,-100]
```

## Important Part

```python
nums[-k:]
```

gets the last `k` elements.

```python
nums[:-k]
```

gets all elements before the last `k` elements.

Combining them gives the rotated array.

## In-Place Modification

The statement:

```python
nums[:] = ...
```

updates the original list instead of assigning a completely new list to the variable.

This is useful because the problem requires the input array to be modified in-place.

## Time Complexity

**O(n)**

The array elements are processed to create the rotated arrangement.

## Space Complexity

**O(n)**

The slicing operation creates a temporary array containing the elements.

## Difficulty

**Medium**

## Topics

* Arrays
* Array Rotation
* In-place Array Manipulation
* Modulo Operation
* Slicing

## What I Learned

This problem helped me understand how to rotate an array efficiently.

The main idea is:

```text
Take last k elements
        ↓
Move them to the front
        ↓
Keep the remaining elements after them
```

Also, using:

```python
k = k % n
```

avoids unnecessary rotations when `k` is larger than the array length.

## Author

T.Nandhini
