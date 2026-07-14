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



---

# 📘 DSA Handbook – Day 2 (HashMap & Set)

## 1. Two Sum (LeetCode 1)

**Pattern:** HashMap (Complement Lookup)

**Problem:**
Given an array and a target, return the indices of two numbers whose sum equals the target.

**Concept Learned:**

* HashMap
* Complement (`target - current`)
* Store **Number → Index**

**Time Complexity:** `O(n)`

---

## 2. Contains Duplicate (LeetCode 217)

**Pattern:** HashSet / Existence Check

**Problem:**
Return `True` if any element appears more than once.

**Concept Learned:**

* Fast lookup using Set
* Checking if an element has already been seen

**Time Complexity:** `O(n)`

---

## 3. Valid Anagram (LeetCode 242)

**Pattern:** Frequency Counting

**Problem:**
Check whether two strings are anagrams.

**Concept Learned:**

* Character → Frequency
* Dictionary comparison
* Building frequency maps

**Time Complexity:** `O(n)`

---

## 4. Majority Element (LeetCode 169)

**Pattern:** Frequency Counting + Running Maximum

**Problem:**
Find the element occurring more than `n/2` times.

**Concept Learned:**

* Number → Frequency
* Find maximum frequency

**Time Complexity:** `O(n)`

---

## 5. Intersection of Two Arrays (LeetCode 349)

**Pattern:** HashSet

**Problem:**
Return all unique common elements.

**Concept Learned:**

* Set lookup
* Unique answers
* Converting Set → List

**Time Complexity:** `O(n + m)`

---

## 6. Longest Consecutive Sequence (LeetCode 128)

**Pattern:** HashSet + Sequence Detection

**Problem:**
Find the length of the longest consecutive sequence.

**Concept Learned:**

* Set for O(1) lookup
* Start only from the beginning of a sequence (`num - 1 not in set`)
* Running maximum

**Time Complexity:** `O(n)`

---

# 📚 Concepts Learned Today

### HashMap

```python
hashmap = {}
```

### Add / Update

```python
hashmap[key] = value
hashmap[key] += 1
```

### Membership

```python
if key in hashmap:
```

---

### Set

```python
s = set()
```

### Add

```python
s.add(x)
```

### Membership

```python
if x in s:
```

---

### Dictionary Equality

```python
dict1 == dict2
```

---

### Frequency Counting Template

```python
hashmap = {}

for x in arr:
    if x in hashmap:
        hashmap[x] += 1
    else:
        hashmap[x] = 1
```

---
# 📘 DSA Handbook – Day 3 (Advanced Two Pointers)

---

# 📚 Questions Solved Today

## 14. Valid Palindrome (LeetCode 125) *(Revision Pending)*

### Pattern

**Two Pointers + Character Filtering**

### Problem

Check whether a string is a palindrome after:

* Ignoring spaces
* Ignoring punctuation
* Ignoring uppercase/lowercase differences

### Core Idea

* Start from both ends.
* Skip invalid characters.
* Compare valid characters.
* Move inward.

### Time Complexity

**O(n)**

---

## 15. Two Sum II (LeetCode 167)

### Pattern

**Opposite-End Two Pointers**

### Problem

Given a **sorted array**, return the indices of two numbers whose sum equals the target.

### Core Idea

```text
left = 0
right = n-1

sum = arr[left] + arr[right]
```

Rules:

```text
sum == target
    return answer

sum < target
    left++

sum > target
    right--
```

### Why it Works

Because the array is sorted.

* Need a bigger sum → move **left**
* Need a smaller sum → move **right**

### Time Complexity

**O(n)**

---

## 16. Container With Most Water (LeetCode 11)

### Pattern

**Two Pointers + Running Maximum**

### Formula

```text
Area = Width × Height
```

Where

```text
Width = right - left

Height = min(height[left], height[right])
```

### Core Idea

Always move the **shorter** wall.

Reason:

* Width always decreases.
* The only chance to increase area is by finding a taller minimum height.

Rule:

```text
height[left] < height[right]
    left++

else
    right--
```

### Time Complexity

**O(n)**

---

## 17. 3Sum (LeetCode 15)

### Pattern

**Sorting + Fixed Element + Two Pointers**

### Core Idea

1. Sort the array.
2. Fix one element.
3. Use Two Sum II on the remaining elements.
4. Skip duplicates.

Visualization:

```text
Sort

↓

Fix nums[i]

↓

left = i+1
right = n-1

↓

Move pointers

↓

Store triplets

↓

Skip duplicates
```

### Time Complexity

Sorting

```text
O(n log n)
```

Searching

```text
O(n²)
```

Overall

```text
O(n²)
```

---

