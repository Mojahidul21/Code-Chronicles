## 🚀 Understanding Fast Exponentiation Using Bitwise Operations

When dealing with very large numbers in programming—such as computing $a^b \mod m$—naively multiplying the base repeatedly becomes slow and prone to overflow. To solve this efficiently, we use a technique called **binary exponentiation** or **exponentiation by squaring**.

---

### 🔍 The Idea

Any positive integer exponent can be represented in binary form. For example:

$$
13 = 1101_2 = 2^3 + 2^2 + 0 + 2^0
$$

So, $a^{13}$ becomes:

$$
a^{13} = a^{8} \cdot a^{4} \cdot a^{1}
$$

Instead of multiplying $a$ 13 times, we square the base and multiply only when the corresponding bit in the exponent is `1`. This reduces the time complexity from **O(b)** to **O(log b)**.

---

### 🧠 Core Concepts Used

* `exponent & 1` checks if the lowest bit is 1.
* `exponent >>= 1` right shifts the exponent (equivalent to dividing by 2).
* `base = (base * base) % mod` efficiently squares the base at each step.
* `result = (result * base) % mod` accumulates the answer when needed.

---

### 💻 C++ Implementation

```cpp
long long modPow(long long base, long long exponent, long long mod) {
    long long result = 1 % mod; // in case mod is 1
    base %= mod;

    while (exponent > 0) {
        if (exponent & 1)
            result = (result * base) % mod;

        base = (base * base) % mod;
        exponent >>= 1;
    }

    return result;
}
```

---

### ✅ Why It Works

* Uses modular arithmetic to avoid overflow.
* Handles large powers in logarithmic time.
* Works for any base and exponent as long as you apply `% mod`.

This method is widely used in competitive programming, cryptography (e.g., RSA), and modular computations.

---
