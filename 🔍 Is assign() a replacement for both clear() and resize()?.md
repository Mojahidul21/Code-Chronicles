### 🔍 Is `assign()` a replacement for both `clear()` and `resize()`?

**Yes — in many cases, `assign()` can *replace* the use of both `clear()` and `resize()` together**, because:

* It **clears** the current contents.
* It **resizes** the container to the new size.
* It **fills** it with the given values.

---

### 🔁 Comparison:

| Function         | Purpose                           | Can `assign()` do it?             |
| ---------------- | --------------------------------- | --------------------------------- |
| `clear()`        | Makes container empty             | ✅ Yes (assign 0 elements)         |
| `resize(n)`      | Changes size to `n`, default-fill | ✅ Yes (assign `n` default values) |
| `assign(n, val)` | Clears, resizes, and fills        | ✅ Does all at once                |

---

### ✅ Example:

Instead of:

```cpp
v.clear();
v.resize(5, 100); // v = {100, 100, 100, 100, 100}
```

You can just write:

```cpp
v.assign(5, 100); // Same result, shorter and more efficient
```

---

### ❗ But remember:

* If you only want to remove elements without adding new ones → use `clear()`
* If you want to change size and preserve part of the data → use `resize()`
* If you're replacing everything → use `assign()`

---


> **`assign()` = `clear()` + `resize()` + `fill` in one shot**
