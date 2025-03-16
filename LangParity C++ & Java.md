# LangParity: C++ and Java : Syntax Comparisons and Operational Differences

## 🎯 Overview
This document outlines the key syntax differences between C++ and Java — a quick reference for anyone switching between the two languages or doing them in parallel as I'm!

---

## 🔧 Basic Syntax Differences

| Feature             | C++                                   | Java                                                     |
|---------------------|---------------------------------------|----------------------------------------------------------|
| **Printing Output** | `cout << "Hello";`                    | `System.out.println("Hello");`                           |
| **Input**           | `cin >> x;`                           | `Scanner sc = new Scanner(System.in); x = sc.nextInt();` |
| **Comments**        | `// single-line` / `/* multi-line */` | `// single-line` / `/* multi-line */`                    |
| **Main Function**   | `int main() {}`                       | `public static void main(String[] args) {}`              |

---

## 🔢 Data Types

| Type         | C++                           | Java                 |
|--------------|-------------------------------|----------------------|
| Integer      | `int`                         | `int`                |
| Float/Double | `float`/`double`              | `float`/`double`     |
| String       | `string` (`#include<string>`) | `String` (capital S) |
| Boolean      | `bool`                        | `boolean`            |

---

## 🔄 Loops

| Loop Type          | C++                               | Java                             |
|--------------------|-----------------------------------|----------------------------------|
| **For Loop**       | `for (int i = 0; i < n; i++) {}`  | `for (int i = 0; i < n; i++) {}` |
| **While Loop**     | `while (condition) {}`            | `while (condition) {}`           |
| **Do-While Loop**  | `do { } while (condition);`       | `do { } while (condition);`      |
| **For-Each Loop**  | `for (auto x : arr) {}` *(C++11)* | `for (Type x : arr) {}`          |

---

## 🔥 Data Structures : Array

| Feature            | C++                           | Java                       |
|--------------------|-------------------------------|----------------------------|
| **Declaration**    | `int arr[5];`                 | `int[] arr = new int[5];`  |
| **Initialization** | `int arr[5] = {1,2,3,4,5};`   | `int[] arr = {1,2,3,4,5};` |
| **Accessing**      | `arr[0]`                      | `arr[0]`                   |
| **Size**           | `sizeof(arr)/sizeof(arr[0])`  | `arr.length`               |

---

## 🔥 Data Structures : Linked List

| Feature           | C++                                             | Java                                        |
|-------------------|-------------------------------------------------|---------------------------------------------|
| **Definition**    | `struct Node { int data; Node* next; };`        | `class Node { int data; Node next; }`       |
| **Node Creation** | `Node* head = new Node();`                      | `Node head = new Node();`                   |
| **Insertion**     | `head->next = new Node();`                      | `head.next = new Node();`                   |
| **Traversal**     | `while(temp != nullptr) { temp = temp->next; }` | `while(temp != null) { temp = temp.next; }` |

---

## 🔥 Data Structures : Vectors (C++) & ArrayList (Java)

| Feature            | C++                | Java                                        |
|--------------------|--------------------|---------------------------------------------|
| **Declaration**    | `vector<int> v;`   | `ArrayList<Integer> v = new ArrayList<>();` |
| **Add Element**    | `v.push_back(10);` | `v.add(10);`                                |
| **Size**           | `v.size()`         | `v.size()`                                  |
| **Access Element** | `v[i]`             | `v.get(i)`                                  |

---

## 🔥 Data Structures : Tree (BST, Skewed Tree - Right-ST + Left-ST, N-Ary Tree)

| Feature           | C++               | Java              |
|-------------------|-------------------|-------------------|
| **Definition**    | `###############` | `###############` |
| **Node Creation** | `###############` | `###############` |
| **Insertion**     | `###############` | `###############` |
| **Traversal**     | `###############` | `###############` |

---

## 🎉 Final Thoughts
This Markdown file serves as a quick yet comprehensive reference to bridge the syntax gap between C++ and Java. Whether you’re prepping for an interview or shifting between languages — efficiency is key! 🚀✨
