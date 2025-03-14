# Contributing to LeetCode-Solutions

Thank you for your interest in contributing to **LeetCode-Solutions**. Our repository is dedicated to providing optimized and well-documented solutions to LeetCode problems in **C++** and **Java**. By contributing, you join a community that values clarity, performance, and thorough documentation, ultimately helping developers improve their problem-solving skills.

---

## Table of Contents

1. [Getting Started](#getting-started)
2. [Workflow Guidelines](#workflow-guidelines)
3. [Coding Standards](#coding-standards)
4. [Documentation & Comments](#documentation--comments)
5. [Testing Guidelines](#testing-guidelines)
6. [Pull Request Process](#pull-request-process)
7. [Advanced Contributions](#advanced-contributions)
8. [Contribution Checklist](#contribution-checklist)
9. [Contact & Support](#contact--support)

---

## Getting Started

1. **Fork the Repository:**  
   Click the **Fork** button at the top right of the repository page to create your own copy.

2. **Clone Your Fork:**  
   Clone the repository locally:
   ```bash
   git clone https://github.com/your-username/LeetCode-Solutions.git
   ```

3. **Configure Upstream:**  
   Set the upstream remote to keep your fork up-to-date:
   ```bash
   cd LeetCode-Solutions
   git remote add upstream https://github.com/original-username/LeetCode-Solutions.git
   ```

---

## Workflow Guidelines

- **Create a Feature Branch:**  
  Always work on a new branch dedicated to your feature, bug fix, or improvement. Use descriptive names such as:
  ```bash
  git checkout -b feature/optimized-two-sum
  ```
  
- **Regularly Sync with Upstream:**  
  Avoid merge conflicts by regularly pulling changes from the upstream repository:
  ```bash
  git fetch upstream
  git merge upstream/main
  ```
  
- **Commit Often:**  
  Make incremental, logically grouped commits with clear and concise commit messages.

---

## Coding Standards

- **Language Conventions:**
  - **C++:** Adhere to modern C++ standards (C++11/14/17). Utilize the STL where applicable and maintain consistency in naming and formatting.
  - **Java:** Follow Java best practices including proper class design, clear method naming, and structured exception handling.

- **File Naming & Directory Structure:**
  - **File Naming:** Name files using the format: `problem_number_problem_title.ext` (e.g., `001_Two_Sum.cpp`).
  - **Directory Structure:**  
    - Contributed code solutions should reside under `Contributor's Contribution/` directory

- **Code Quality:**
  - Write modular, maintainable code with minimal duplication.
  - Avoid magic numbers—use constants or enumerations where appropriate.
  - Ensure robust error handling and validate edge cases.

---

## Documentation & Comments

- **Problem Summary:**  
  At the top of each solution file, provide a brief summary of the problem statement.

- **Approach Explanation:**  
  Detail your solution strategy, including algorithm design, complexity analysis (both time and space), and key decision points.

- **Inline Comments:**  
  Use inline comments to clarify complex logic or non-obvious code segments. Ensure comments are concise and relevant.

- **References:**  
  When applicable, include links to external resources or related discussions that provide further insight into the problem.

---

## Testing Guidelines

- **Local Testing:**  
  Verify your solution using multiple test cases, including edge and corner cases, before committing.

- **Edge Case Consideration:**  
  Ensure your code gracefully handles minimal, maximal, and invalid input scenarios. Document these cases as inline comments.

- **Unit Testing:**  
  While not mandatory, contributions that include unit tests or benchmarks to validate performance are highly appreciated.

---

## Pull Request Process

1. **Push Your Changes:**  
   Once your changes are complete and tested, push your branch to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```

2. **Open a Pull Request (PR):**  
   Submit a PR against the `main` branch of the original repository. Your PR should include:
   - A clear, descriptive title summarizing the changes.
   - A detailed description covering:
     - The problem addressed.
     - Your approach and reasoning.
     - Performance and complexity considerations.
     - Any issues or edge cases handled.
   - References to related issues or LeetCode problem numbers, if applicable.

3. **Code Review:**  
   Engage with maintainers during the review process. Address any feedback and be open to making revisions to improve your contribution.

---

## Advanced Contributions

- **Algorithm Optimization:**  
  Propose alternative approaches that improve time or space complexity, or enhance code clarity.

- **Design Patterns & Refactoring:**  
  Apply design patterns to improve code modularity or readability. Refactor existing solutions to follow best practices.

- **Extended Documentation:**  
  Enhance problem explanations and provide additional context, including performance benchmarks or detailed walkthroughs.

- **New Problem Categories:**  
  Contribute by organizing or introducing new problem categories that expand the repository’s scope.

---

## Contribution Checklist

Before submitting your PR, please ensure that:

- [x] The code compiles and executes as expected.
- [x] Commit messages are clear and descriptive.
- [x] Your changes conform to the repository's coding standards and structure.
- [x] Each solution file includes a concise problem description, approach explanation, and complexity analysis.
- [x] Edge cases and potential pitfalls have been thoroughly tested.
- [x] Documentation is complete and aligns with the project's overall style.
- [x] Your branch is rebased with the latest upstream changes to avoid merge conflicts.
- [x] Any new directories or categories follow the existing structure and naming conventions.

---

## Contact & Support

For questions, suggestions, or further discussion, please open an issue in the repository or contact a maintainer directly.

---

Thank you for contributing to **LeetCode-Solutions**. Your expertise and dedication make this repository a valuable resource for developers worldwide.

Happy coding!
