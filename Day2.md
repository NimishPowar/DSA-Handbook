# DSA Handbook – Day 2 (HashMap & Set)

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

# Concepts Learned Today

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
