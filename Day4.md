# DSA Handbook – Day 4 (Sliding Window)

# Questions Solved Today

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

# Concepts Learned Today

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
