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
# 📘 DSA Handbook – Day 4 (Sliding Window)

---

# 📚 Questions Solved Today

## 18. Maximum Sum Subarray of Size K

### Pattern

**Fixed Size Sliding Window**

### Problem

Given an array and a window size `k`, find the **maximum sum** of any contiguous subarray of size `k`.

Example:

```text
Input:
arr = [2,1,5,1,3,2]
k = 3

Output:
9
```

---

### Brute Force

For every starting index:

* Calculate the sum of the next `k` elements.
* Keep the maximum.

Time Complexity:

```text
O(n × k)
```

---

### Optimized Idea

Instead of calculating every window from scratch:

```text
Old Window

[2 1 5]

↓

New Window

[1 5 1]
```

Only two things happen:

* One element leaves.
* One element enters.

Formula:

```python
window_sum = window_sum - arr[i-k] + arr[i]
```

---

### Algorithm

1. Calculate the first window.
2. Store it in `max_sum`.
3. Slide the window.
4. Update `max_sum`.

---

### Java Version (First Window)

```java
int windowSum = 0;

for(int i = 0; i < k; i++){
    windowSum += arr[i];
}

int maxSum = windowSum;
```

---

### Time Complexity

```text
O(n)
```

---

## 19. Maximum Average Subarray I

### Pattern

**Fixed Size Sliding Window**

### Observation

Average is simply:

```text
Average = Sum / k
```

Since `k` is fixed,

finding the **maximum average** is the same as finding the **maximum sum**.

---

### Common Mistake

❌ Wrong

```python
window_avg = window_avg - outgoing + incoming
```

This doesn't work because the sliding formula applies to **sums**, not averages.

---

### Correct Approach

Track:

```python
window_sum
```

After finding the maximum:

```python
return max_sum / k
```

---

### Time Complexity

```text
O(n)
```

---

## 20. Longest Substring Without Repeating Characters

### Pattern

**Variable Size Sliding Window + HashSet**

---

### Problem

Find the length of the longest substring containing only unique characters.

Example:

```text
abcabcbb

↓

abc

Answer = 3
```

---

### Core Idea

Expand the window using `right`.

If a duplicate appears,

shrink the window using `left`

until the window becomes valid again.

---

### Template

```python
left = 0
seen = set()

for right in range(len(s)):

    while s[right] in seen:
        seen.remove(s[left])
        left += 1

    seen.add(s[right])

    max_len = max(max_len, right - left + 1)
```

---

### Why `while` instead of `if`?

Some duplicates require removing **multiple** characters.

Example:

```text
abba
```

Using only `if`:

```text
Remove 'a'

Window = "bb"

Still duplicate ❌
```

Using `while`:

```text
Remove 'a'

Still duplicate

↓

Remove first 'b'

Valid ✅
```

Rule:

```text
Use while when the window must keep shrinking until it becomes valid.
```

---

### Time Complexity

```text
O(n)
```

Each character is added and removed at most once.

---

# 🧠 Concepts Learned Today

---

## 1. Fixed Size Sliding Window

Window size never changes.

```text
[2 1 5]

↓

[1 5 1]

↓

[5 1 3]
```

Template:

```python
window_sum = first_window

for i in range(k, len(arr)):
    window_sum = window_sum - arr[i-k] + arr[i]
```

---

## 2. Variable Size Sliding Window

Window grows.

If it becomes invalid,

shrink it.

Template:

```python
for right in range(len(arr)):

    while invalid:
        left += 1

    update_answer()
```

---

## 3. Two Types of Sliding Window

| Fixed Window  | Variable Window                        |
| ------------- | -------------------------------------- |
| Size is fixed | Size changes                           |
| Mostly arrays | Mostly strings                         |
| Sum / Average | Unique chars, frequencies, constraints |

---

## 4. Sliding Window Update Formula

This is the most important line from today's session:

```python
window_sum = window_sum - outgoing + incoming
```

For arrays:

```python
window_sum = window_sum - arr[i-k] + arr[i]
```

---

## 5. Window Length Formula

For every variable sliding window:

```python
current_length = right - left + 1
```

Use this instead of relying on `len(set)`.

---

