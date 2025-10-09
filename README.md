# 📚 Learning DSA — My Notes & Explanations

Welcome to my **Data Structures and Algorithms (DSA)** learning repository!  
This repo is my personal space to take structured notes, write explanations, and document problem-solving patterns — all in clean Markdown format.  

I’m learning concepts one topic at a time and writing them here for quick revision and long-term reference.  
Each section will include:
- 📘 Core concept explanation  
- 💡 Example code (in Python/JavaScript)  
- ⏱️ Time and Space Complexity  
- 🧩 Common patterns and interview notes  

---

## 🎯 Learning Resources

I’m following and learning DSA from the following sources:

- 🌐 **[algomap.io](https://algomap.io)** — interactive DSA roadmap and concept visualizer  
- ▶️ **[YouTube Playlist](https://www.youtube.com/playlist?list=PLKYEe2WisBTFEr6laH5bR2J19j7sl5O8R)** — structured DSA video series  
- 📝 Notes are written and organized **according to the above roadmap and playlist flow**


> ⚙️ Repository Goal: Build a clear, well-organized set of DSA notes that grow as I progress — from basics to advanced topics like graphs, recursion, and dynamic programming.

---

_🧠 Formatting, structure, and Markdown layout styled with help from **ChatGPT (GPT-5)** for readability and consistency._

---

# 🧠 Notes on **Time & Space Complexity + Big O Notation**

---

## 📍 1.1 What is Time Complexity?

**Time Complexity** measures how the *execution time* of an algorithm grows with the size of the input `n`.

It’s not measured in seconds — it’s measured in **number of operations**.

---

### Example 1 – Square all numbers in an array

```python
def square(arr):
    result = []
    for num in arr:
        result.append(num ** 2)
    return result
```

* The loop runs once for each element.
* For an array of `n` elements → we do `n` operations.

✅ **Time Complexity:** `O(n)` → *Linear time*
📈 As `n` doubles, time doubles.

---

### Example 2 – Find all pairs of numbers

You generate every pair `(a, b)` in the array.

```python
def all_pairs(arr):
    pairs = []
    for i in range(len(arr)):
        for j in range(i + 1, len(arr)):
            pairs.append((arr[i], arr[j]))
    return pairs
```

* Outer loop runs `n` times
* Inner loop runs up to `n` times for each outer iteration

✅ **Time Complexity:** `O(n²)` → *Quadratic time*
📈 As `n` doubles, time increases 4×.

---

## 🧾 1.2 Visualizing Time Complexities

| Type         | Big O        | Shape on Graph             | Example                     |
| ------------ | ------------ | -------------------------- | --------------------------- |
| Constant     | `O(1)`       | Horizontal line            | Access first element        |
| Linear       | `O(n)`       | Straight diagonal line     | Loop through array          |
| Quadratic    | `O(n²)`      | Steep parabola             | Nested loops                |
| Cubic        | `O(n³)`      | Even steeper curve         | 3 nested loops              |
| Logarithmic  | `O(log n)`   | Slowly rising curve        | Binary search               |
| Linearithmic | `O(n log n)` | Between linear & quadratic | Merge sort, quick sort      |
| Exponential  | `O(2ⁿ)`      | Explosive growth           | Recursive subset generation |
| Factorial    | `O(n!)`      | Impossible for large n     | Permutations                |

---

## 🧩 1.3 Understanding Big O

**Big O Notation** describes the *upper bound* — the *worst-case* growth rate of an algorithm.

It basically asks:

> “Can I draw a function that’s always equal to or **worse** (grows faster) than my algorithm?”

---

### Example:

If algorithm A takes `n` operations
→ it’s `O(n)`

If algorithm B takes `n²` operations
→ it’s `O(n²)`
and it’s **not** `O(n)` because no straight line can bound a parabola from above.

---

## 🧮 1.4 Simplifying Big O Expressions

We drop:

* **Constants** → because they don’t affect growth rate
* **Lower-order terms** → because they’re negligible as `n` grows

---

### Example:

```
O(n² + 2n + 1) → O(n²)
O(5n²) → O(n²)
O(3n³ + 5n²) → O(n³)
```

Why?

> As `n → ∞`, the *highest power of n* dominates.

---

## 💾 1.5 Space Complexity

**Space Complexity** measures how much *extra memory* your algorithm needs.

---

### Example 1 – Creating a new array

```python
def square(arr):
    result = []
    for num in arr:
        result.append(num ** 2)
    return result
```

* Uses extra space proportional to size of input → `O(n)`

---

### Example 2 – Modifying the array in-place

```python
def square_in_place(arr):
    for i in range(len(arr)):
        arr[i] = arr[i] ** 2
    return arr
```

* Doesn’t create a new array
  ✅ **Space Complexity:** `O(1)` → *Constant space*

---

## ⚡ 1.6 Constant Time Operations (`O(1)`)

Operations that take the same amount of time **no matter the input size**.

Examples:

* Accessing `arr[0]`
* Returning first element
* Printing a fixed number
* Simple arithmetic operations
* Hash lookups (average case)

---

### Note:

`O(1)` ≠ “one operation”
→ it just means **constant number of operations** (like 3, 5, etc.), not dependent on `n`.

Example:

```python
a[0], a[1], a[2]  # still O(1)
```

---

## 📉 1.7 Typical Growth Rates (From Best to Worst)

| Complexity   | Name         | Common Example          |
| ------------ | ------------ | ----------------------- |
| `O(1)`       | Constant     | Accessing array index   |
| `O(log n)`   | Logarithmic  | Binary search           |
| `O(n)`       | Linear       | Single loop             |
| `O(n log n)` | Linearithmic | Merge sort, quick sort  |
| `O(n²)`      | Quadratic    | Nested loops            |
| `O(n³)`      | Cubic        | 3 nested loops          |
| `O(2ⁿ)`      | Exponential  | Recursion on subsets    |
| `O(n!)`      | Factorial    | Permutations generation |

---

## ⚙️ 1.8 Big O Laws (Quick Rules)

1. **Drop constants:**
   `O(2n)` → `O(n)`

2. **Drop smaller terms:**
   `O(n² + n)` → `O(n²)`

3. **Multiplying loops:**

   ```
   for i in range(n):
       for j in range(n):
           ...
   ```

   → `O(n²)`

4. **Sequential loops:**

   ```
   for i in range(n):
       ...
   for j in range(n):
       ...
   ```

   → `O(n) + O(n)` = `O(n)`

---

## 🧱 1.9 Quick Summary of Examples

| Operation            | Time Complexity | Space Complexity |
| -------------------- | --------------- | ---------------- |
| Access array element | O(1)            | O(1)             |
| Loop through array   | O(n)            | O(1)             |
| Nested loop (pairs)  | O(n²)           | O(n²)            |
| Create new array     | O(n)            | O(n)             |
| Modify in place      | O(n)            | O(1)             |
| Binary search        | O(log n)        | O(1)             |
| Merge sort           | O(n log n)      | O(n)             |

---

## 🧠 1.10 Final Takeaways

* **Time Complexity** → how long your code runs
* **Space Complexity** → how much memory it uses
* **Big O Notation** → upper bound on growth
* **Ignore constants and lower-order terms**
* **Aim for**:

  * O(1) → Best
  * O(log n) → Great
  * O(n) → Good
  * Avoid O(n²)+ unless absolutely necessary

# 🧩 2. Static Arrays, Dynamic Arrays, and Strings

> 🧠 **Learning Source:**  
> - 🎥 [YouTube Lecture – Arrays & Strings (by AlgoMap)](https://youtu.be/TQMvBTKn2p0?si=-0-7E9Yvnp-Hf8tl)

---

## 📍 2.1 Static Arrays

### 🔹 Definition

A **static array** is a **contiguous block of memory with a fixed size**.  
Once created, its size **cannot be changed**.  
Each element is accessed using an **index** from `0` to `length - 1`.

---

### 🧩 Example

```text
Array a = [1, 2, 3, 4, 5]
Indices = 0  1  2  3  4
Length = 5
````

---

### ⚙️ 2.1.1 Common Operations & Time Complexity

| Operation         | Description                         | Time Complexity |
| ----------------- | ----------------------------------- | --------------- |
| Access `a[i]`     | Directly read an element at index i | **O(1)**        |
| Update `a[i] = x` | Modify value at index i             | **O(1)**        |
| Search `x in a`   | Scan through all elements           | **O(n)**        |
| Insert            | Shift elements to make room         | **O(n)**        |
| Delete            | Shift elements to fill gap          | **O(n)**        |

---

### 🧠 2.1.2 Key Notes

* Static arrays are **mutable** (values can change) but **fixed in size**.
* Memory is **contiguous**, enabling **constant-time access**.
* Useful when you know the data size in advance.

---

## ⚙️ 2.2 Dynamic Arrays

### 🔹 Definition

A **dynamic array** can **grow or shrink** in size.
It’s built using a static array underneath — when full, it **creates a new larger array** and **copies elements over**.

---

### 🧩 Example (Python)

```python
a = [1, 2, 3]
a.append(4)   # O(1) average (amortized)
a.insert(1, 5)  # O(n)
a.pop()  # O(1)
```

---

### 🧮 2.2.1 How Dynamic Arrays Grow

* When full, a **new array with double capacity** is created.
* All elements are **copied** to the new array.
* This resizing is costly, but happens **rarely**.

---

### ⚙️ 2.2.2 Operation Complexity

| Operation            | Description                 | Time Complexity                                 |
| -------------------- | --------------------------- | ----------------------------------------------- |
| Access `a[i]`        | Direct lookup               | **O(1)**                                        |
| Update `a[i] = x`    | Modify element              | **O(1)**                                        |
| Append `a.append(x)` | Add at end                  | **O(1)** (amortized) / **O(n)** (during resize) |
| Pop                  | Remove last element         | **O(1)**                                        |
| Insert (not end)     | Shift elements              | **O(n)**                                        |
| Delete (not end)     | Shift elements              | **O(n)**                                        |
| Search `x in a`      | Scan for element            | **O(n)**                                        |
| Length `len(a)`      | Return stored size property | **O(1)**                                        |

---

### 🔹 2.2.3 Amortized Complexity

Even though resizing is `O(n)`, it happens infrequently.
So the **average cost per append** = **O(1)** (called **amortized O(1)**).

---

## 💬 2.3 Strings

### 🔹 Definition

A **string** is essentially an **array of characters**.
In Python, strings are **immutable**, meaning you **cannot change** them once created.

---

### 🧩 Example

```python
s = "abc"
```

* Stored as contiguous characters in memory.
* Any change (like concatenation) creates a **new string**.

---

### ⚙️ 2.3.1 Common Operations & Complexity

| Operation             | Description                        | Time Complexity        |
| --------------------- | ---------------------------------- | ---------------------- |
| Access `s[i]`         | Get character at index i           | **O(1)**               |
| Concatenate `s + "x"` | Create new string (copy all chars) | **O(n)**               |
| Check `'a' in s`      | Search for character               | **O(n)**               |
| Insert/Delete         | Not possible directly              | **O(n)** (via copying) |
| Length `len(s)`       | Get pre-stored length              | **O(1)**               |

---

### 🧩 Example (Python)

```python
s = "hello"
b = s + "z"   # O(n), creates 'helloz'
'e' in s      # O(n), search
len(s)        # O(1)
```

---

## 🧾 2.4 Summary Chart

| Data Structure           | Operation                | Avg Time | Notes             |
| ------------------------ | ------------------------ | -------- | ----------------- |
| **Static Array**         | Access / Modify          | O(1)     | Fixed size        |
|                          | Insert / Delete          | O(n)     | Requires shifting |
| **Dynamic Array (List)** | Append (end)             | O(1)*    | Amortized         |
|                          | Insert / Delete (middle) | O(n)     | Shifting required |
|                          | Access / Modify          | O(1)     | Direct index      |
|                          | Search                   | O(n)     | Sequential scan   |
| **String (Immutable)**   | Access                   | O(1)     | Immutable         |
|                          | Append / Modify          | O(n)     | New copy created  |
|                          | Search `'x' in s`        | O(n)     | Sequential scan   |

---

## 💡 2.5 Key Takeaways

* **Static Arrays:** Fixed size, fast access, efficient memory layout.
* **Dynamic Arrays:** Flexible size with **amortized O(1)** appends.
* **Strings (in Python):** Immutable — any modification creates a new copy.
* `len()` for both arrays and strings is **O(1)** since size is stored internally.
* Dynamic arrays grow by **doubling capacity** when full.

---

📚 **Next Topic → 3. Linked Lists** (coming up next in the DSA roadmap)

---


