# A Complete Guide to Sorting in C++

Sorting is a fundamental operation in programming, particularly useful in problem solving and data organization. The C++ Standard Library provides robust and flexible ways to sort containers like `vector`, `array`, and even custom data structures such as `tuple` and `struct`.

In this article, we'll explore:

1. Sorting basic data types
2. Custom sorting using lambda functions
3. Custom sorting with structs
4. Sorting with tuples
5. Stable sorting
6. Indirect sorting (sorting indices)
7. Summary of best practices

---

## 1. Sorting Basic Data Types

Sorting a vector of integers in ascending or descending order is straightforward using `std::sort` from the `<algorithm>` header:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> a = {5, 2, 9, 1, 3};
    sort(a.begin(), a.end()); // Ascending
    // sort(a.begin(), a.end(), greater<int>()); // Descending
    for (int x : a) cout << x << ' ';
}
```

---

## 2. Custom Sorting Using Lambda Functions

When sorting complex data like pairs or custom conditions, lambdas offer inline comparison logic:

```cpp
vector<pair<int, int>> v = {{1, 3}, {2, 2}, {4, 1}};
sort(v.begin(), v.end(), [](pair<int, int> a, pair<int, int> b) {
    return a.second < b.second;
});
```

You can also sort in descending order or by multiple keys (e.g., sort by `a.second`, then by `a.first`):

```cpp
sort(v.begin(), v.end(), [](auto &a, auto &b) {
    return (a.second == b.second) ? a.first < b.first : a.second < b.second;
});
```

---

## 3. Custom Sorting With Structs

If you have a struct, you can overload the `<` operator or provide a custom comparator:

```cpp
struct Student {
    int id;
    string name;
};

bool cmp(const Student &a, const Student &b) {
    return a.name < b.name; // Sort alphabetically by name
}

vector<Student> students = {{1, "Alice"}, {2, "Bob"}, {3, "Charlie"}};
sort(students.begin(), students.end(), cmp);
```

---

## 4. Sorting With Tuples

Tuples can hold multiple data fields of different types. To sort by a specific element (e.g., the 2nd one):

```cpp
vector<tuple<int, int, int>> data = {{1, 5, 10}, {2, 3, 8}, {3, 9, 6}};
sort(data.begin(), data.end(), [](auto &a, auto &b) {
    return get<1>(a) < get<1>(b);
});
```

You can also sort by multiple keys:

```cpp
sort(data.begin(), data.end(), [](auto &a, auto &b) {
    return (get<1>(a) == get<1>(b)) ? get<2>(a) < get<2>(b) : get<1>(a) < get<1>(b);
});
```

---

## 5. Stable Sorting

Use `std::stable_sort` if you want to maintain the relative order of equivalent elements:

```cpp
stable_sort(data.begin(), data.end(), [](auto &a, auto &b) {
    return get<1>(a) < get<1>(b);
});
```

It is slightly slower than `sort` (uses O(n log^2 n)), but very useful when tie-breaking based on original order is important.

---

## 6. Indirect Sorting (Sorting Indices)

Sometimes you want to sort based on values without changing the original array. You can sort the indices instead:

```cpp
vector<int> a = {50, 20, 40, 30};
vector<int> idx(a.size());
iota(idx.begin(), idx.end(), 0);

sort(idx.begin(), idx.end(), [&](int i, int j) {
    return a[i] < a[j];
});

// Print elements in sorted order without modifying 'a'
for (int i : idx) cout << a[i] << ' ';
```

---

## 7. Summary of Best Practices

| Use Case                          | Recommended Method                   |
| --------------------------------- | ------------------------------------ |
| Basic sort (int, float, etc.)     | `sort(begin, end)`                   |
| Descending order                  | `sort(begin, end, greater<T>())`     |
| Sort by custom logic              | `sort(begin, end, lambda)`           |
| Sort structs                      | Custom comparator or overloaded `<`  |
| Sort tuples                       | Use `get<i>(tuple)` inside lambda    |
| Stable sort (tie-break preserved) | `stable_sort(begin, end, lambda)`    |
| Indirect sort                     | Sort index vector using a comparator |

---

This article serves as a handy reference to understand and apply sorting in C++ efficiently. Store it, practice it, and master it!
