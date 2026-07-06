# DSA-Handbook

# DSA Arrays Revision Sheet (Day 1)

## Question 1: Find the Largest Element in an Array

### Problem

Given an array of integers, return the largest element.

### Example

```python
arr = [12, 45, 7, 89, 23, 56]
```

Output:

```python
89
```

### Solution

```python
def max_ele(arr):
    if len(arr) == 0:
        return None

    max_value = arr[0]

    for i in range(len(arr)):
        if arr[i] > max_value:
            max_value = arr[i]

    return max_value
```

**Pattern:** Running Maximum

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Question 2: Find the Second Largest Element

### Problem

Return the second largest element in an array.

### Example

```python
arr = [12, 45, 7, 89, 23, 56]
```

Output

```python
56
```

### Solution

```python
def second_largest(arr):
    if len(arr) < 2:
        return None

    largest = float("-inf")
    second = float("-inf")

    for num in arr:
        if num > largest:
            second = largest
            largest = num
        elif largest > num > second:
            second = num

    return second
```

**Pattern:** Running Maximum

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Question 3: Reverse an Array

### Problem

Reverse an array in-place.

### Example

```python
[2,4,6,8,10]
```

Output

```python
[10,8,6,4,2]
```

### Solution

```python
def reverse(arr):
    left = 0
    right = len(arr)-1

    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1

    return arr
```

**Pattern:** Two Pointers

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Question 4: Move Zeroes to the End

### Problem

Move all zeroes to the end while maintaining the order of non-zero elements.

### Example

```python
[0,1,0,3,12]
```

Output

```python
[1,3,12,0,0]
```

### Solution

```python
def move_zeroes(arr):
    insert = 0

    for i in range(len(arr)):
        if arr[i] != 0:
            arr[insert] = arr[i]
            insert += 1

    for i in range(insert, len(arr)):
        arr[i] = 0

    return arr
```

**Pattern:** Reader–Writer

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Question 5: Remove Duplicates from a Sorted Array

### Problem

Remove duplicates in-place from a sorted array and return the number of unique elements.

### Example

```python
[1,1,2,2,3,4,4,5]
```

After execution:

```python
[1,2,3,4,5,_,_,_]
```

Return:

```python
5
```

### Solution

```python
def remove_duplicates(arr):
    if len(arr) == 0:
        return 0

    insert = 1

    for i in range(1, len(arr)):
        if arr[i] != arr[i-1]:
            arr[insert] = arr[i]
            insert += 1

    return insert
```

**Pattern:** Reader–Writer

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Question 6: Rotate Array by One Position (Right)

### Problem

Rotate an array to the right by one position.

### Example

```python
[1,2,3,4,5]
```

Output

```python
[5,1,2,3,4]
```

### Solution

```python
def rotate(arr):
    if len(arr) <= 1:
        return arr

    temp = arr[-1]

    for i in range(len(arr)-1, 0, -1):
        arr[i] = arr[i-1]

    arr[0] = temp

    return arr
```

**Pattern:** Shifting Elements

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Question 7: Best Time to Buy and Sell Stock

### Problem

Buy once and sell once to maximize profit.

### Example

```python
[7,1,5,3,6,4]
```

Output

```python
5
```

### Solution

```python
def max_profit(prices):
    if len(prices) == 0:
        return 0

    min_price = prices[0]
    max_profit = 0

    for i in range(1, len(prices)):
        if prices[i] < min_price:
            min_price = prices[i]
        else:
            profit = prices[i] - min_price
            if profit > max_profit:
                max_profit = profit

    return max_profit
```

**Pattern:** Running Minimum

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

# Patterns Learned Today

| Question                      | Pattern           |
| ----------------------------- | ----------------- |
| Largest Element               | Running Maximum   |
| Second Largest                | Running Maximum   |
| Reverse Array                 | Two Pointers      |
| Move Zeroes                   | Reader–Writer     |
| Remove Duplicates             | Reader–Writer     |
| Rotate Array                  | Shifting Elements |
| Best Time to Buy & Sell Stock | Running Minimum   |

---

# Tomorrow's Revision Plan

Without looking at the solutions:

1. Find Largest Element
2. Find Second Largest Element
3. Reverse an Array
4. Move Zeroes
5. Remove Duplicates from Sorted Array
6. Rotate Array by One Position
7. Best Time to Buy and Sell Stock

Only check the solution if you're completely stuck.

After finishing these, move on to:

* Two Sum
* Contains Duplicate
* Valid Anagram
* Intersection of Two Arrays

These will introduce the **HashMap** pattern.
