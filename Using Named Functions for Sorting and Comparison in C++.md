# 📘 Using Named Functions for Sorting and Comparison in C++

In C++, sorting a collection like a `vector` is often done using the `std::sort()` function from the `<algorithm>` library. While lambda functions are commonly used for custom sorting, **named functions** provide a clean, readable, and reusable alternative.

---

## 📌 What is a Named Function?

A **named function** is just a regular C++ function declared with a name (as opposed to anonymous functions like lambdas).

```cpp
bool compare(int a, int b) {
    return a < b;
}
```

This function can be reused in multiple contexts — especially when the logic is complex or used frequently.

---

## ✅ Syntax of `std::sort`

```cpp
std::sort(start_iterator, end_iterator, comparator_function);
```

* `start_iterator` – beginning of the range to sort.
* `end_iterator` – one past the last element to sort.
* `comparator_function` *(optional)* – custom logic to decide order.

If no comparator is provided, `std::sort` uses the default `<` operator.

---

## 🧠 Why Use Named Functions for Sorting?

* ✅ Improves **readability**
* 🔁 Encourages **code reuse**
* 🧪 Helps **test/debug** independently
* 📦 Keeps lambdas from cluttering the code

---

## ✨ Examples

### 🔹 1. Sort a Vector in Descending Order

```cpp
bool descending(int a, int b) {
    return a > b;
}

int main() {
    std::vector<int> v = {4, 1, 5, 2, 3};
    std::sort(v.begin(), v.end(), descending);

    for (int x : v) std::cout << x << " ";
}
```

### 🔹 2. Sort a Vector of Pairs by Second Element

```cpp
bool sortBySecond(const std::pair<int, int>& a, const std::pair<int, int>& b) {
    return a.second < b.second;
}

int main() {
    std::vector<std::pair<int, int>> vp = {{1, 20}, {2, 10}, {3, 30}};
    std::sort(vp.begin(), vp.end(), sortBySecond);

    for (auto [f, s] : vp) std::cout << f << ":" << s << "\n";
}
```

---

### 🔹 3. Sort Vector of Tuples by 2nd Element

```cpp
bool sortBySecondElement(const std::tuple<int, int, int>& a, const std::tuple<int, int, int>& b) {
    return std::get<1>(a) < std::get<1>(b);
}

int main() {
    std::vector<std::tuple<int, int, int>> vt = {
        {1, 50, 100}, {2, 30, 200}, {3, 40, 300}
    };

    std::sort(vt.begin(), vt.end(), sortBySecondElement);

    for (auto [x, y, z] : vt)
        std::cout << x << "," << y << "," << z << "\n";
}
```

---

## 🔄 Sorting with Struct and Function Object

If you're dealing with more structured data, using a struct with a comparison operator is a good alternative.

```cpp
struct Thief {
    int gold, id;
};

bool compareGold(const Thief& a, const Thief& b) {
    return a.gold < b.gold;
}
```

Then:

```cpp
std::vector<Thief> v;
std::sort(v.begin(), v.end(), compareGold);
```

This approach works great when you’re using `struct` instead of `tuple`.

---

## 💡 Tips

* **Function signature must match** what `std::sort` expects:
  `bool func(const T& a, const T& b)`

* The function should return `true` if `a` should come before `b`.

* Avoid modifying elements inside the comparator — it's meant for **comparison only**.

---

## 🔁 Comparison: Lambda vs Named Function

| Feature       | Lambda                     | Named Function                 |
| ------------- | -------------------------- | ------------------------------ |
| ✅ Readability | ✘ (for long logic)         | ✅ (named & reusable)           |
| ✅ Reusability | ✘ (repeated code)          | ✅                              |
| ✅ Debuggable  | ✘ (harder to isolate/test) | ✅ (easy to test independently) |
| ✅ Verbosity   | ✅ (short)                  | ✘ (extra lines, but clear)     |

---

## 📎 When to Prefer Named Functions?

* Logic is **complex**
* Sorting is done **in multiple places**
* You want to **unit test** the comparator
* You're working in a **team** or preparing for **long-term maintenance**

---

## 🧾 Summary

Named functions are:

* ✅ Easy to read and debug
* ✅ Powerful in sorting and comparison
* ✅ Useful across `vector`, `pair`, `tuple`, `struct`, etc.
* ✅ Often better than lambda when logic is non-trivial

Use them freely when sorting with custom criteria — they'll make your code more maintainable and clear.

---
