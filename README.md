# LeetCode-Solutions
<svg width="95" height="111" viewBox="0 0 95 111" fill="none" xmlns="http://www.w3.org/2000/svg" class="h-full w-auto max-w-none"><path d="M68.0063 83.0664C70.5 80.5764 74.5366 80.5829 77.0223 83.0809C79.508 85.579 79.5015 89.6226 77.0078 92.1127L65.9346 103.17C55.7187 113.371 39.06 113.519 28.6718 103.513C28.6117 103.456 23.9861 98.9201 8.72653 83.957C-1.42528 74.0029 -2.43665 58.0749 7.11648 47.8464L24.9282 28.7745C34.4095 18.6219 51.887 17.5122 62.7275 26.2789L78.9048 39.362C81.6444 41.5776 82.0723 45.5985 79.8606 48.3429C77.6488 51.0873 73.635 51.5159 70.8954 49.3003L54.7182 36.2173C49.0488 31.6325 39.1314 32.2622 34.2394 37.5006L16.4274 56.5727C11.7767 61.5522 12.2861 69.574 17.6456 74.8292C28.851 85.8169 37.4869 94.2846 37.4969 94.2942C42.8977 99.496 51.6304 99.4184 56.9331 94.1234L68.0063 83.0664Z" fill="#FFA116"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M41.1067 72.0014C37.5858 72.0014 34.7314 69.1421 34.7314 65.615C34.7314 62.0879 37.5858 59.2286 41.1067 59.2286H88.1245C91.6454 59.2286 94.4997 62.0879 94.4997 65.615C94.4997 69.1421 91.6454 72.0014 88.1245 72.0014H41.1067Z" fill="#B3B3B3"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M49.9118 2.02335C52.3173 -0.55232 56.3517 -0.686894 58.9228 1.72277C61.494 4.13244 61.6284 8.17385 59.2229 10.7495L16.4276 56.5729C11.7768 61.552 12.2861 69.5738 17.6453 74.8292L37.4088 94.2091C39.9249 96.6764 39.968 100.72 37.505 103.24C35.042 105.761 31.0056 105.804 28.4895 103.337L8.72593 83.9567C-1.42529 74.0021 -2.43665 58.0741 7.1169 47.8463L49.9118 2.02335Z" fill="black"></path></svg>
A curated repository of optimized solutions for LeetCode challenges implemented in **C++** and **Java**. This repository serves as a reference for algorithmic problem solving, interview preparation, and mastering data structures.

---

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Languages and Tools](#languages-and-tools)
- [Usage](#usage)
- [Contributing](#contributing)
- [Code Quality](#code-quality)
- [License](#license)

---

## Overview

**LeetCode-Solutions** is a collection of well-documented, efficient, and clean code solutions to a wide array of LeetCode problems. Each solution is accompanied by explanations that highlight the approach, complexity analysis, and any relevant edge cases. The main focus is on providing clear, modular code written in **C++** and **Java** to facilitate learning and review.

---

## Project Structure

The repository is organized by programming language and then by problem categories:

```
LeetCode-Solutions/
├── LeetCode-Streak/
│   ├── Daily Questions 1
│   | 
│   .
│   .
│   .
│   .
│   |
|   └── Daily Questions n
|
├── Solutions/
│   ├── Two-Sum.md/
│   ├── Add-Two-Numbers.md/
│   .
│   .
│   .
│   |
│   └── n<sup>th</sup> Question
|
├── CONTRIBUTING.md
├── LICENSE
├── LeetCode-Solutions-Index.md
└── README.md
```

- **LeetCode-Streak Folder:** Contains LeetCode's Daily Challenge Problem's Solution -- Maintaining Streak
  - **File Naming:** Solutions are named by their LeetCode problem number and title for easy navigation
- **Solutions Folder:** Contains LeetCode's Problems solved using languages either `C++` or `Java` or both
  - **File Naming:** Solutions are named by their LeetCode problem title for easy navigation.
- **Documentation Files:**
  - **README.md:** Provides an overview and usage instructions.
  - **CONTRIBUTING.md:** Outlines guidelines for contributing to the repository.
  - **LeetCode-Solutions-Index.md:** Outlines guidelines for accessing question's solution easily -- Indexing

---

## Languages

- **C++:** Utilizes modern C++ standards (e.g., C++11/14/17) and STL for robust and optimized solutions.
- **Java:** Emphasizes clarity and efficiency using core Java libraries.
---

## Usage

### Compiling and Running Solutions

#### C++ Example

To compile a C++ solution (for example, the Two Sum problem):

> Compilation
```bash
g++ -std=c++17 -o solution 001_Two_Sum.cpp
```
then
> Execution
```bash
./solution
```

or
> Compilation
```bash
g++ 001_Two_Sum.cpp
```
then
> Execution
```bash
./a.exe
```

#### Java Example

To compile and run a Java solution (for example, the Two Sum problem):
> Compilation
```bash
javac 001_Two_Sum.java
```
then
> Execution
```bash
java 001_Two_Sum
```

Feel free to adapt the commands based on your system configuration and project structure.

---

## Contributing

Contributions are welcome! If you’d like to add a new solution, improve an existing one, or fix any issues, please follow these steps:

1. **Fork the Repository:** Create your own fork of the project.
2. **Create a Branch:** Use a descriptive name for your branch (e.g., `feature/add-two-sum-solution`).
3. **Commit Changes:** Follow the coding style used in the repository. Include comments explaining your approach and complexity.
4. **Submit a Pull Request:** Provide a clear description of your changes and reference any related LeetCode problems.

Please review our [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on code style, commit messages, and testing.

---

## Code Quality

Each solution in this repository includes:

- **Problem Description:** A concise summary of the LeetCode problem.
- **Approach Explanation:** Detailed comments that explain the logic, algorithm, and complexity (both time and space).
- **Clean Code:** Emphasis on readability, modular design, and best practices.
- **Test Cases:** Example inputs and expected outputs are provided when applicable to verify the solution.

---

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute the code as long as proper attribution is provided.

---

Happy coding and best of luck on your journey to mastering algorithms and data structures!
