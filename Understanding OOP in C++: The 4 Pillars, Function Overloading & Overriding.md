# 🔹 Understanding OOP in C++: The 4 Pillars, Function Overloading & Overriding

C++ is a powerful language widely used in **competitive programming** and **system-level development**, and it fully supports **Object-Oriented Programming (OOP)**. At the heart of OOP are four fundamental concepts:

* **Encapsulation**
* **Inheritance**
* **Abstraction**
* **Polymorphism**

Understanding these concepts not only helps you write clean, modular, and reusable code but also lays the foundation for mastering advanced techniques like **function overloading** and **function overriding**.

---

## 🔐 1. Encapsulation – Data Hiding and Access Control

**Encapsulation** refers to wrapping data (variables) and methods (functions) that operate on that data into a single unit — typically a class. It also **restricts direct access** to internal data using access specifiers like `private`, `public`, and `protected`.

### 🧾 Example:

```cpp
class Student {
private:
    int marks;  // private data

public:
    void setMarks(int m) {
        if (m >= 0 && m <= 100) marks = m;
    }

    int getMarks() {
        return marks;
    }
};
```

**Why it matters:** Encapsulation protects internal object states and only exposes what’s necessary — a critical principle in both design and security.

---

## 👪 2. Inheritance – Reusability of Code

**Inheritance** allows a new class (derived/child class) to inherit properties and behaviors from an existing class (base/parent class). This avoids code duplication and fosters reuse.

### 🧾 Example:

```cpp
class Animal {
public:
    void eat() {
        cout << "Eating...\n";
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking...\n";
    }
};
```

**Why it matters:** Reusability saves time and creates a hierarchy of classes, making complex programs manageable.

---

## 🎯 3. Abstraction – Hiding Complex Implementation

**Abstraction** focuses on exposing only the necessary features and hiding internal details. In C++, you can achieve abstraction using **interfaces** (i.e., abstract classes with pure virtual functions).

### 🧾 Example:

```cpp
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle\n";
    }
};
```

**Why it matters:** Abstraction simplifies complexity and lets you focus on what an object does instead of how it does it.

---

## 🎭 4. Polymorphism – Many Forms

**Polymorphism** means “many forms.” In C++, polymorphism allows you to use a single interface to represent different types or behaviors.

### Two main types:

#### 🔹 a. Compile-time Polymorphism (Function Overloading)

Multiple functions with the same name but different **parameters** in the same scope.

```cpp
class Printer {
public:
    void show(int a) {
        cout << "Integer: " << a << "\n";
    }

    void show(string s) {
        cout << "String: " << s << "\n";
    }
};
```

**This is called:** Function Overloading
**Resolved at:** Compile time

---

#### 🔹 b. Run-time Polymorphism (Function Overriding)

A derived class redefines a **base class function** using the same signature. The base class function must be marked `virtual`.

```cpp
class Base {
public:
    virtual void greet() {
        cout << "Hello from Base\n";
    }
};

class Derived : public Base {
public:
    void greet() override {
        cout << "Hello from Derived\n";
    }
};
```

In `main()`:

```cpp
Base* ptr = new Derived();
ptr->greet();  // Output: Hello from Derived
```

**This is called:** Function Overriding
**Resolved at:** Runtime (via virtual dispatch)

---

## 🔄 Recap Table

| Concept       | Purpose                           | Key Feature                | Example Keyword               |
| ------------- | --------------------------------- | -------------------------- | ----------------------------- |
| Encapsulation | Hides data, provides safe access  | Class with private members | `private`, `public`           |
| Inheritance   | Reuses code from a base class     | Derived classes            | `class B : public A`          |
| Abstraction   | Hides internal details            | Abstract class / Interface | `virtual`, `= 0`              |
| Polymorphism  | One interface, multiple behaviors | Overloading & Overriding   | `virtual`, multiple functions |

---

## 🧩 All Concepts Together in One Program

```cpp
#include <iostream>
using namespace std;

// Abstraction + Polymorphism
class Shape {
public:
    virtual void draw() = 0; // Pure virtual = Abstraction
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle\n";
    }
};

// Inheritance + Encapsulation
class Student {
private:
    int marks;

public:
    void setMarks(int m) { marks = m; }
    int getMarks() { return marks; }
};

// Function Overloading
class Printer {
public:
    void print(int x) { cout << "Integer: " << x << "\n"; }
    void print(string s) { cout << "String: " << s << "\n"; }
};

// Function Overriding
class Base {
public:
    virtual void greet() { cout << "Hello from Base\n"; }
};

class Derived : public Base {
public:
    void greet() override { cout << "Hello from Derived\n"; }
};

int main() {
    // Encapsulation
    Student s;
    s.setMarks(95);
    cout << "Marks: " << s.getMarks() << "\n";

    // Abstraction + Polymorphism
    Shape* shape = new Circle();
    shape->draw();
    delete shape;

    // Overloading
    Printer p;
    p.print(42);
    p.print("OOP");

    // Overriding
    Base* b = new Derived();
    b->greet();
    delete b;
}
```

---

## ✅ Final Words

In C++ and competitive programming, mastering OOP helps you:

* Write cleaner, modular, and maintainable code.
* Understand and use the Standard Template Library (STL) more effectively.
* Build simulations, game logic, and system designs with ease.

Once you truly understand **Encapsulation, Inheritance, Abstraction, and Polymorphism**, advanced topics like **virtual tables**, **interface design**, and even **design patterns** will come naturally.

---
