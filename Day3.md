# DSA Handbook – Day 3 (Advanced Two Pointers)

# Questions Solved Today

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
