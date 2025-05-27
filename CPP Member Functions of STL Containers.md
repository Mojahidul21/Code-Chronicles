Here's an article titled:

---

## **C++ Member Functions of STL Containers: Explained with Examples**

C++ Standard Template Library (STL) provides a variety of containers like `vector`, `list`, `deque`, `map`, `set`, etc., that help developers manage collections of data efficiently. Each container comes with a set of **member functions** that allow performing common operations like inserting, deleting, resizing, and accessing elements.

This article focuses on **commonly used member functions** of **sequence containers** (like `vector`, `deque`, `list`) and **associative containers** (like `set`, `map`).

---

### 🔹 1. `assign()`

Replaces the current contents of the container with new values.

#### Syntax:

```cpp
container.assign(count, value);     // fills with 'value', 'count' times
container.assign(first, last);      // copies from another container or array
```

#### Example:

```cpp
vector<int> v;
v.assign(4, 100);  // v becomes {100, 100, 100, 100}
```

---

### 🔹 2. `clear()`

Removes all elements from the container. The size becomes 0, but memory may still be reserved.

#### Syntax:

```cpp
container.clear();
```

#### Example:

```cpp
deque<int> d = {1, 2, 3};
d.clear();  // d becomes empty
```

---

### 🔹 3. `resize()`

Changes the size of the container. If increased, new elements are added with default values or a given value.

#### Syntax:

```cpp
container.resize(new_size);
container.resize(new_size, value);
```

#### Example:

```cpp
vector<int> v = {1, 2, 3};
v.resize(5);         // v = {1, 2, 3, 0, 0}
v.resize(3);         // v = {1, 2, 3}
v.resize(6, 99);     // v = {1, 2, 3, 99, 99, 99}
```

---

### 🔹 4. `size()` and `capacity()`

* `size()` returns the number of elements in the container.
* `capacity()` returns the allocated storage size (only for containers like `vector` and `deque`).

#### Example:

```cpp
vector<int> v = {10, 20};
cout << v.size();     // Output: 2
cout << v.capacity(); // Might be more than 2
```

---

### 🔹 5. `empty()`

Returns `true` if the container has no elements.

#### Example:

```cpp
list<int> l;
if (l.empty()) {
    cout << "List is empty\n";
}
```

---

### 🔹 6. `push_back()` / `push_front()`

Adds an element to the end or beginning of the container (where applicable).

#### Example:

```cpp
deque<int> dq;
dq.push_back(10);     // adds to back
dq.push_front(5);     // adds to front
```

---

### 🔹 7. `pop_back()` / `pop_front()`

Removes the last or first element (only in containers that support it like `deque` and `list`).

---

### 🔹 8. `insert()` and `erase()`

* `insert()` adds an element at a specific position.
* `erase()` removes an element or range.

#### Example:

```cpp
vector<int> v = {1, 2, 4};
v.insert(v.begin() + 2, 3); // v = {1, 2, 3, 4}
v.erase(v.begin() + 1);     // v = {1, 3, 4}
```

---

### 🔹 9. `begin()` and `end()`

Return iterators pointing to the start and one past the end of the container.

---

### 🔹 10. `find()` (Associative Containers)

Used to search for an element.

#### Example:

```cpp
set<int> s = {1, 2, 3};
if (s.find(2) != s.end()) {
    cout << "Found\n";
}
```

---

## 🧠 Summary Table

| Function      | Purpose                       | Commonly Used In              |
| ------------- | ----------------------------- | ----------------------------- |
| `assign()`    | Replace content               | `vector`, `deque`, `list`     |
| `clear()`     | Remove all elements           | All containers                |
| `resize()`    | Change the size               | `vector`, `deque`, `string`   |
| `empty()`     | Check if container is empty   | All containers                |
| `size()`      | Return number of elements     | All containers                |
| `capacity()`  | Return allocated storage size | `vector`, `deque`             |
| `insert()`    | Insert at specific position   | `vector`, `list`, `set`, etc. |
| `erase()`     | Remove element or range       | `vector`, `list`, `map`, etc. |
| `find()`      | Search for value              | `set`, `map`, `unordered_map` |
| `push_back()` | Add element at end            | `vector`, `deque`, `list`     |
| `pop_back()`  | Remove last element           | `vector`, `deque`, `list`     |

---

## ✅ Final Thoughts

Understanding the STL member functions is essential for efficient C++ programming. These functions help manage container data with minimal effort and maximum efficiency. To master them, practice with real problems using containers like `vector`, `list`, and `map`.

---
