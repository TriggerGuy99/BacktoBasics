# Back to Basics: The Professional Standard

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](LICENSE)
[![Code style: Black](https://img.shields.io/badge/code%20style-black-000000?style=for-the-badge)](https://github.com/psf/black)
[![Linting: Flake8](https://img.shields.io/badge/linting-flake8-4B8BBE?style=for-the-badge)](https://flake8.pycqa.org/)

> **Bridging the gap from "Script Kiddie" to "Software Engineer."**

This repository is the **companion code** to the *Back to Basics* YouTube series,a deep re-examination of Python fundamentals through the lens of **professional software engineering standards**. We don't just teach syntax. We teach **memory models**, **type safety**, **defensive coding**, and the **Trigger Standard**: the non-negotiable rules that separate amateurs from professionals.

---

## 🛑 The Rules of Engagement

Every line of code in this repository follows these commandments:

- **🔒 Strict Type Hinting** — No naked variables. Every function declares its contract:
  ```python
  def calculate_area(width: float, height: float) -> float:
  ```

- **📋 PEP 8 Compliance** — Code is automatically formatted with **Black** and validated with **Flake8**. Formatting arguments are over.

- **🧠 Memory Awareness** — We understand Stack vs Heap, mutable vs immutable, references vs copies. No `id()` hacks.

- **🛡️ Defensive Coding** — Guard clauses replace nested `if/else`. Fail fast, return early.
  ```python
  if not user:
      return "Invalid user"
  # Only happy path here
  ```

- **🚫 No Global Scope** — All executable code lives inside `if __name__ == "__main__":`. Modules are libraries, not scripts.

- **📚 Complete Docstrings** — Every function has a Google-style docstring explaining the *why*, not just the *what*.

---

## 📚 The Curriculum

| Module | Title | Key Concepts | Status |
|--------|-------|--------------|--------|
| **00_Prerequisites** | 🧱 The Rust Remover | Memory Model, PEP 8, Mutable vs Immutable | 🟢 Complete |
| **01_Strings** | 🔤 The String Architect | ASCII, Manual Parsing, `ord()`, String Methods | 🟡 In Progress |
| **02_Lists** | 📊 The Data Crusher | Algorithms, Error Handling, Matrix Logic, Sorting | 🔴 Planned |
| **03_Dicts_Sets** | 🔑 The Hash Master | O(1) Lookups, Hashing, Merging Data, Caching | 🔴 Planned |
| **04_Logic** | 🎲 The Logic Gate | Nested Loops, Math, Visual Patterns, Recursion | 🔴 Planned |
| **05_OOP** | 🏗️ The Class Architect | `self` vs `cls`, `@staticmethod`, Inheritance, Polymorphism | 🔴 Planned |
| **06_Advanced** | 🔮 The Meta-Programmer | Decorators (`@`), Wrappers, Context Managers, I/O | 🔴 Planned |

**Status Legend:** 🟢 Complete | 🟡 In Progress | 🔴 Planned

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.10 or higher**
- **Git**
- A terminal (bash/zsh/PowerShell)

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/TriggerGuy99/Back-to-Basics-Python.git
cd Back-to-Basics-Python
```

#### 2. Create a Virtual Environment

```bash
# Create the virtual environment
python -m venv venv

# Activate it
# On Linux/macOS:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

#### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

This installs:
- **Black** — Code formatter (PEP 8 automation)
- **Flake8** — Linter (style compliance)
- **mypy** — Type checker (optional but recommended)

#### 4. Verify Setup

```bash
python --version  # Should be 3.10+
black --version
flake8 --version
```

---

## 📖 How to Use This Repository

### For Learners
1. Navigate to a module (e.g., `00_Prerequisites/`).
2. Read `NOTES.md` for the deep concepts.
3. Study the example files (`*.py`).
4. Attempt the exercises.
5. Refer to `solutions/` only after you've tried.

### For Educators
- All code follows the **Trigger Standard** explicitly.
- Use this as a reference for what "professional Python" looks like.
- The NOTES.md files are standalone lessons—presentable to any audience.

---

## 🎯 The Philosophy: "Trigger Standard"

The **Trigger Standard** is our shared standard for professional code:

```
┌─────────────────────────────────────────┐
│    S: Strict Type Hinting              │
│    T: Tests & Type Checking            │
│    A: ASCII & Algorithm Awareness      │
│    N: No Global Scope                  │
│    D: Defensive Coding (Guard Clauses) │
│    A: Automated Linting (Black/Flake8) │
│    R: Readable & DRY Code              │
│    D: Docstrings & Documentation       │
└─────────────────────────────────────────┘
```

Every module reinforces these principles. By the end, you won't just *know* Python—you'll **think** like a software engineer.

---

## 🧪 Running Examples

Each module contains runnable examples:

```bash
cd 00_Prerequisites
python examples/memory_model.py
```

All examples include:
- Type hints
- Docstrings
- Guard clauses
- Error handling

---

## 🤝 Contributing

This is an **open-source educational repository**. Contributions are welcome!

### Guidelines
- All code must follow the **Trigger Standard**.
- Run Black and Flake8 before committing:
  ```bash
  black .
  flake8 .
  ```
- Include docstrings and type hints.
- Update NOTES.md if you add new concepts.

---

## 📝 License

This repository is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---

## 🎬 Related Resources

- **YouTube Series:** [Back to Basics](https://youtube.com/yourchannellink)
- **Book:** *Professional Python* (coming soon)
- **Community:** Join our Discord for questions and discussions

---

## 🎓 Final Word

> *"Code is read 100 times more often than it is written."*

Every function, every variable, every line of code you write is a conversation with future developers—most likely yourself, six months from now, exhausted at 2 AM, trying to fix a bug.

**Make their life easy. Make your future self proud.**

Write code to the **Trigger Standard**. 🏆

---

**Last Updated:** February 2026 | **Maintainer:** The Back to Basics Team
