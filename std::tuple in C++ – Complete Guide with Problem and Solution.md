# 📦 `std::tuple` in C++ – Complete Guide with Problem and Solution

## 🔹 What is a `tuple`?

A `tuple` is a fixed-size collection that can hold **multiple values of different types**. It’s like `std::pair`, but extended to support more than two elements.

`tuple` is part of the C++ Standard Library (`<tuple>` header) and was introduced in **C++11**.

---

## 🧾 Basic Syntax

```cpp
#include <tuple>

tuple<int, string, float> t1(1, "hello", 3.14);
auto t2 = make_tuple(42, "banana", 2.71);
```

---

## 🔍 Accessing and Modifying Elements

```cpp
cout << get<0>(t1);       // 1
get<1>(t1) = "world";     // Modify second element
```

---

## 🔄 Structured Binding (C++17+)

```cpp
auto [a, b, c] = t1; // Unpacks the tuple into variables
```

---

## 🧮 Tuple Size & Element Type

```cpp
tuple<int, double, char> t;
cout << tuple_size<decltype(t)>::value; // Output: 3

using T = tuple_element<1, decltype(t)>::type; // T is double
```

---

## 📚 Use Case in Competitive Programming

You often want to **return multiple values** from a function (like min, max, and sum), or **store compound values** in a container for sorting or processing.

---

# ✅ Problem: Student Records Sorting

**Problem Statement:**

You are given information about `N` students. Each student has:

* An ID (int)
* A name (string)
* A CGPA (float)

You need to **sort the students**:

1. First by **descending CGPA**
2. If CGPA is equal, then by **ascending name**
3. If both CGPA and name are equal, then by **ascending ID**

Print the sorted list of students.

---

### 🔧 Sample Input:

```
5
1001 Alice 3.9
1002 Bob 3.7
1003 Alice 3.9
1004 David 3.7
1005 Eve 4.0
```

### 🔍 Sample Output:

```
1005 Eve 4
1001 Alice 3.9
1003 Alice 3.9
1002 Bob 3.7
1004 David 3.7
```

---

## 🧠 Solution Using `tuple`

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<tuple<float, string, int>> students; // (cgpa, name, id)

    for (int i = 0; i < n; ++i) {
        int id;
        string name;
        float cgpa;
        cin >> id >> name >> cgpa;
        
        students.push_back(make_tuple(-cgpa, name, id)); // Negative CGPA for descending sort
    }

    sort(students.begin(), students.end());

    for (auto &[cgpa, name, id] : students) {
        cout << id << " " << name << " " << -cgpa << "\n";
    }
}
```

---

## 🔎 Explanation

* `tuple<float, string, int>` is used to store the student information.
* We store `-cgpa` to sort it in **descending** order since default `sort()` is ascending.
* `sort()` works lexicographically on tuples:

  1. First by `-cgpa` (descending CGPA)
  2. Then by `name` (ascending)
  3. Then by `id` (ascending)

---

## 📌 Summary Table

| Feature                       | Description                  |
| ----------------------------- | ---------------------------- |
| `make_tuple(a, b, c)`         | Create a tuple               |
| `get<i>(t)`                   | Access element               |
| `structured bindings`         | Unpack tuple easily (C++17+) |
| `tuple_size`, `tuple_element` | For compile-time reflection  |
| `sort(vector<tuple<...>>)`    | Lexicographical sorting      |

---
