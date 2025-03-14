# LangParity: C++ and Java : Syntax Comparisons and Operational Differences

## 🎯 Overview
This document outlines the key syntax differences between C++ and Java — a quick reference for anyone switching between the two languages or doing them in parallel as I'm

---

## 🔧 Basic Syntax Differences

| Feature            | C++ Syntax               | Java Syntax               |
|--------------------|--------------------------|---------------------------|
| **Printing Output** | `cout << "Hello";`       | `System.out.println("Hello");` |
| **Input**           | `cin >> x;`              | `Scanner sc = new Scanner(System.in); x = sc.nextInt();` |
| **Comments**       | `// single-line` / `/* multi-line */` | `// single-line` / `/* multi-line */` |
| **Main Function**   | `int main() {}`          | `public static void main(String[] args) {}` |

---

## 🔢 Data Types

| Type         | C++    | Java    |
|--------------|--------|---------|
| Integer      | `int`  | `int`   |
| Float/Double | `float`/`double` | `float`/`double` |
| String       | `string` (`#include<string>`) | `String` (capital S) |
| Boolean      | `bool` | `boolean` |

---

## 🛠️ String Operations

| Operation        | C++ Syntax            | Java Syntax              |
|------------------|-----------------------|--------------------------|
| **Length**        | `str.size()` or `str.length()` | `str.length()`           |
| **Concatenation** | `str1 + str2`         | `str1.concat(str2)` or `str1 + str2` |
| **Substring**     | `str.substr(start, len)` | `str.substring(start, end)` |
| **Character Access** | `str[i]`           | `str.charAt(i)`          |

---

## 🔄 Loops

| Loop Type         | C++ Syntax                         | Java Syntax                         |
|-------------------|-----------------------------------|------------------------------------|
| **For Loop**       | `for (int i = 0; i < n; i++) {}`   | `for (int i = 0; i < n; i++) {}`    |
| **While Loop**     | `while (condition) {}`            | `while (condition) {}`              |
| **Do-While Loop**  | `do { } while (condition);`       | `do { } while (condition);`         |
| **For-Each Loop**  | `for (auto x : arr) {}` *(C++11)* | `for (Type x : arr) {}`             |

---

## 🧠 Conditionals

| Condition Type     | C++ Syntax          | Java Syntax         |
|--------------------|---------------------|---------------------|
| **If-Else**         | `if (condition) {}` | `if (condition) {}` |
| **Else-If**         | `else if (cond) {}` | `else if (cond) {}` |
| **Ternary Operator**| `condition ? a : b` | `condition ? a : b` |

---

## 🚀 Exception Handling

| Feature            | C++ Syntax                 | Java Syntax                    |
|--------------------|----------------------------|-------------------------------|
| **Try-Catch Block** | `try { ... } catch(...) {}` | `try { ... } catch(Exception e) {}` |
| **Throw Exception** | `throw 404;`               | `throw new Exception("Error");`    |

---

## 🏗️ Functions/Methods

| Feature        | C++ Syntax                     | Java Syntax                        |
|----------------|--------------------------------|-----------------------------------|
| **Function Declaration** | `int add(int a, int b)`     | `int add(int a, int b)`               |
| **Return Statement** | `return a + b;`              | `return a + b;`                      |
| **Void Function**    | `void display()`             | `void display()`                     |
| **Function Call**    | `add(3, 4)`                  | `add(3, 4)`                          |

---

## 🏗️ Classes and Objects

| Feature            | C++ Syntax                                   | Java Syntax                                     |
|--------------------|----------------------------------------------|--------------------------------------------------|
| **Class Definition** | `class MyClass { ... };`                    | `class MyClass { ... }`                           |
| **Object Creation** | `MyClass obj;`                               | `MyClass obj = new MyClass();`                    |
| **Constructor**    | `MyClass() {}` *(Defined inside class)*       | `MyClass() {}` *(Defined inside class)*           |
| **Access Modifiers** | `public`, `private`, `protected`            | `public`, `private`, `protected`, *default*       |

---

## 🔥 Memory Management

| Feature          | C++ Syntax                      | Java Syntax                    |
|------------------|---------------------------------|-------------------------------|
| **Memory Allocation** | `int* ptr = new int;`          | `int[] arr = new int[10];`     |
| **Memory Deallocation** | `delete ptr;`                | *Garbage Collection (Automatic)* |

---

## 🎉 Final Thoughts
This Markdown file serves as a quick yet comprehensive reference to bridge the syntax gap between C++ and Java. Whether you’re prepping for an interview or shifting between languages — efficiency is key! 🚀✨

