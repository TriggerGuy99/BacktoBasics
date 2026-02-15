
# 00 Prerequisites: Back to Basics 🚀

> **Welcome to The Trigger Standard.** This is where Script Kiddies transform into Professional Python Engineers.

---

## 1. PEP 8: The Senior Engineer’s Law

PEP 8 is not a suggestion—**it’s the law for professional Python code**. Here are the strict standards you must memorize to pass a Senior Code Review:

### A. Indentation & Layout

#### Spaces, Not Tabs
**Rule:** Use **4 spaces** per indentation level. Never use tabs.

**Why?** Tabs display differently across editors:
- Some editors show tabs as 2 spaces
- Others show tabs as 8 spaces
- This causes code to look correct on your screen but broken on someone else's

```python
# 🟢 Correct: 4 spaces per level
def process_data(items):
    for item in items:
        if item.is_valid:
            result = item.process()
            return result
```

#### Line Length
**Rule:** Limit all lines to **79 characters**.

**Why?** Allows two code files side-by-side on a standard monitor without horizontal scrolling.

```python
# 🔴 Too long (95 characters)
user_data = calculate_user_statistics(user_id, include_historical=True, format_output=True, verbose=True)

# 🟢 Better: break into multiple lines
user_data = calculate_user_statistics(
    user_id,
    include_historical=True,
    format_output=True,
    verbose=True
)
```

#### Blank Lines
**Rules:**
- **2 blank lines** before a class definition
- **2 blank lines** before top-level function definitions
- **1 blank line** before method definitions inside a class

```python
import os
import sys


def helper_function():
    pass


class MyClass:
    """Example class."""

    def method_one(self):
        pass

    def method_two(self):
        pass


class AnotherClass:
    pass
```

### B. Naming Conventions (The "Case" System)

| Type      | Format         | Example                        |
|-----------|---------------|--------------------------------|
| Variables | `snake_case`   | `user_login_count = 5`         |
| Functions | `snake_case`   | `def calculate_mass():`        |
| Classes   | `CapWords`     | `class SolarSystem:`           |
| Constants | `ALL_CAPS`     | `SPEED_OF_LIGHT = 299792458`   |
| Modules   | `short_lowercase` | `import numpy`              |
| Private   | `_leading_underscore` | `_internal_id = 10`     |

**This is the most common failure point for beginners.**

### C. Whitespace (Breathing Room)

Code must not be claustrophobic. Proper spacing makes code readable.

#### Around Operators
**Rule:** Always put **one space** around assignment and comparison operators.

```python
# 🔴 Bad: cramped and hard to read
x=y+5
if x>10and y<20:
    z=x*y

# 🟢 Good: breathing room
x = y + 5
if x > 10 and y < 20:
    z = x * y
```

#### Function Calls & Definitions
**Rule:** No spaces around `=` in keyword arguments, but spaces around `=` in default parameter values.

```python
# 🔴 Bad: spaces in wrong places
def complex ( real , imag = 0.0 ):
    return magic( real = real , imag = imag )

# 🟢 Good: correct spacing
def complex(real, imag=0.0):
    return magic(real=real, imag=imag)
```

#### After Commas
**Rule:** Always put a space after commas, never before.

```python
# 🔴 Bad
my_list = [1,2,3,4]
my_dict = {'a':1,'b':2}

# 🟢 Good
my_list = [1, 2, 3, 4]
my_dict = {'a': 1, 'b': 2}
```

### D. Imports

Imports must be at the **top of the file**, grouped in this specific order:

1. **Standard Library** imports (built-in modules like os, sys, math)
2. **Third-Party** imports (installed packages like numpy, pandas, requests)
3. **Local Application** imports (your own modules)

**Each group separated by a blank line.**

```python
# 🟢 Correct import order
# 1. Standard library
import os
import sys
from pathlib import Path

# 2. Third-party
import numpy as np
import pandas as pd
import requests

# 3. Local application
from .models import User
from .utils import calculate_hash
from . import config

# 🔴 Wrong: all mixed together
import requests
from .models import User
import os
import numpy as np
```

**Why does this matter?**
- **Instant diagnosis:** If your script crashes due to a missing import, you immediately know:
  - Standard library issue = Python installation problem
  - Third-party issue = Missing package (run `pip install`)
  - Local issue = Project structure problem
- **Merge conflicts:** Reduces git merge conflicts when multiple developers add imports
- **Readability:** Clear separation of external dependencies vs internal code

---

## 2. Python Interpreters & Editors: How They Differ

Python code runs the same everywhere, but **editor and interpreter behaviors can affect your experience**:

| Environment      | Indentation Handling | Linting/Formatting | Execution Style         | Notes |
|------------------|---------------------|--------------------|-------------------------|-------|
| **Vim/Neovim**   | Manual, tabs/spaces | Optional (plugins) | Terminal, script-based  | Easy to misalign code if not careful |
| **VS Code**      | Auto (configurable) | Built-in/Extensions| Interactive, script, notebook | PEP 8 tools available, auto-formatting |
| **Google Colab** | Auto (spaces)       | Some, not strict   | Notebook cells          | Great for demos, less strict on style |
| **Replit**       | Auto (spaces)       | Some, not strict   | Interactive, web-based  | Good for beginners, less control |
| **Jupyter**      | Auto (spaces)       | Some, not strict   | Notebook cells          | Focus on experimentation, not always strict |
| **Other IDEs**   | Varies              | Varies             | Varies                  | Always check settings |

**Key Takeaway:**
- Always check your editor’s settings for tabs vs spaces, auto-formatting, and linting. Inconsistent settings lead to code that fails reviews or even fails to run.

---

## 3. Virtual Environments: Your Safety Net

**Never install Python packages globally unless you know exactly what you’re doing.**

### Why Use Virtual Environments?

- **Isolation:** Each project gets its own dependencies. No version clashes.
- **Safety:** Prevents accidental modification of global libraries (which can break system tools or package managers like `dnf`).
- **Reproducibility:** Others can recreate your environment exactly.

### How to Create One (with `venv`)

```bash
python3 -m venv .venv
source .venv/bin/activate
# Now install packages: pip install requests
```

**Deactivate with:** `deactivate`

**Summary:**
- Virtual environments are essential for professional Python development. They keep your projects clean, safe, and reproducible—no matter your OS or editor.

---

## 4. Memory Management: The "Deep" Knowledge 🧠

### The Core Truth: Variables are References (Tags), NOT Boxes

**Most Script Kiddies think:** *Variables store data.*

**The Reality:** *Variables store memory addresses. They're tags pointing to objects.*

### Memory Model Diagram

```mermaid
graph TB
    subgraph STACK["🔷 STACK (References)"]
        a_ref["a ─────────┐"]
        b_ref["b ─────────┤"]
    end
    
    subgraph HEAP["🔶 HEAP (Actual Data)"]
        list_obj["[1, 2, 3]<br/>id: 0x7f1234"]
    end
    
    a_ref -->|points to| list_obj
    b_ref -->|points to| list_obj
    
    style STACK fill:#e1f5ff
    style HEAP fill:#fff3e0
```

### What This Means

```python
# When you write:
a = [1, 2, 3]
b = a

# You're NOT copying the list!
# Both 'a' and 'b' are TAGS pointing to the SAME object in HEAP

# Proof:
print(id(a) == id(b))  # True! Same object!
b.append(4)
print(a)  # [1, 2, 3, 4] ⚠️ BOTH changed!
```

### Mutable vs Immutable: Critical Distinction

```mermaid
graph LR
    A["🔴 MUTABLE<br/>List, Dict, Set"] -->|Can change in place| B["Dangerous if shared"]
    C["🟢 IMMUTABLE<br/>Int, Str, Tuple"] -->|Cannot change| D["Safe to share"]
```

| Type | Mutability | Why It Matters |
|------|-----------|---|
| **List** | 🔴 Mutable | Modifying shared refs = bugs |
| **Dict** | 🔴 Mutable | Same danger as lists |
| **Set** | 🔴 Mutable | Same danger as lists |
| **Tuple** | 🟢 Immutable | Safe to share; hashable |
| **Int/Str** | 🟢 Immutable | Safe everywhere |

### ⚠️ The `id()` Warning

```python
# DON'T do this in production:
if id(obj1) == id(obj2):
    # This is NOT how you check equality!
    pass

# DO this instead:
if obj1 == obj2:
    # This checks VALUE equality
    pass
```

---

## 5. The Big 4 Data Structures: Quick Revision

Master these four. Everything else is a variation.

| Type | Mutable? | Ordered? | Duplicate Values? | Syntax | Use Case |
|------|----------|----------|---|--------|----------|
| **List** | ✅ Yes | ✅ Yes | ✅ Allowed | `[1, 2, 2]` | Sequences, collections, stacks |
| **Tuple** | ❌ No | ✅ Yes | ✅ Allowed | `(1, 2, 2)` | Fixed data, dict keys, returns |
| **Set** | ✅ Yes | ❌ No | ❌ Unique | `{1, 2}` | Membership, deduplication |
| **Dict** | ✅ Yes | ✅ Yes* | Keys: No, Values: Yes | `{'a': 1}` | Lookups, mappings, caching |

*Dicts are ordered since Python 3.7

### Quick Examples

```python
# List: ordered, mutable
items = [1, 2, 3, 2]  # Duplicates allowed ✅

# Tuple: ordered, immutable
coords = (10, 20)  # Can be a dict key ✅
data = (1, 2, [3, 4])  # List inside? Mutable part is still mutable! ⚠️

# Set: unordered, unique
unique = {1, 2, 3}  # Duplicates removed automatically
# set_obj = {{1: 'a'}}  # ❌ Unhashable type!

# Dict: key-value pairs
cache = {'user_1': 100, 'user_2': 200}  # Fast lookups: O(1)
```

---

## 6. Control Flow: The Anti-Nest Strategy

### The Problem: "Arrow Code"

Nested conditionals are the enemy of readability.

```diff
❌ BAD: Arrow Code (Hard to Follow)
def process_user(user):
    if user:
        if user.is_active:
            if user.balance > 0:
                if user.verified:
                    return "Process payment"
        else:
            return "Account inactive"
    else:
        return "User not found"

✅ GOOD: Guard Clauses (Flat, Clear, Professional)
def process_user(user):
    # Guard clauses: fail fast, return early
    if not user:
        return "User not found"
    if not user.is_active:
        return "Account inactive"
    if user.balance <= 0:
        return "Insufficient balance"
    if not user.verified:
        return "User not verified"
    
    # Only happy path here—crystal clear!
    return "Process payment"
```

### Why Guard Clauses Win

| Metric | Arrow Code | Guard Clauses |
|--------|-----------|---|
| **Readability** | 🔴 Low (nested tunnels) | 🟢 High (linear flow) |
| **Testing** | 🔴 Hard (many branches) | 🟢 Easy (exit early) |
| **Maintenance** | 🔴 Risky (easy to break) | 🟢 Safe (modifications isolated) |
| **Cognitive Load** | 🔴 High | 🟢 Low |

---

## 7. Loops: The Pythonic Way

### The Anti-Pattern: Index-Based Loops

```diff
❌ BAD: C-Style Loop (Scriptish)
items = ['apple', 'banana', 'cherry']
for i in range(len(items)):
    print(f"{i}: {items[i]}")

✅ GOOD: Direct Iteration (Pythonic)
items = ['apple', 'banana', 'cherry']
for item in items:
    print(item)

✅ EVEN BETTER: enumerate() for Index + Value
items = ['apple', 'banana', 'cherry']
for index, item in enumerate(items, start=1):
    print(f"{index}: {item}")

✅ PROFESSIONAL: Dictionary Unpacking
data = [{'id': 1, 'name': 'Alice'}, {'id': 2, 'name': 'Bob'}]
for item_id, name in [d.values() for d in data]:
    print(f"ID: {item_id}, Name: {name}")
```

### Looping Patterns to Master

```python
# 1. With index
for index, item in enumerate(items):
    pass

# 2. Multiple iterables
for name, score in zip(names, scores):
    pass

# 3. Dictionary iteration
for key, value in data.items():
    pass

# 4. Range with step
for i in range(0, 100, 5):  # Every 5th number
    pass

# 5. Reversed
for item in reversed(items):
    pass
```

---

## 8. Functions: The Contract

Functions are **contracts**. They declare:
- **What goes in** (type hints)
- **What comes out** (return types)
- **Why it exists** (docstrings)

### The Gold Standard: Type Hints + Docstrings

```python
def calculate_area(width: float, height: float) -> float:
    """Calculate the area of a rectangle.
    
    This function computes the area using the standard formula:
    area = width × height. Both dimensions must be positive.
    
    Args:
        width (float): The width of the rectangle in units.
                      Must be greater than 0.
        height (float): The height of the rectangle in units.
                       Must be greater than 0.
    
    Returns:
        float: The calculated area in square units.
    
    Raises:
        ValueError: If width or height is non-positive.
    
    Examples:
        >>> calculate_area(5.0, 3.0)
        15.0
        >>> calculate_area(0, 10)
        ValueError: Dimensions must be positive
    """
    if width <= 0 or height <= 0:
        raise ValueError("Dimensions must be positive")
    
    return width * height
```

### Contrast: Good vs Bad

```diff
❌ BAD: Script Kiddie (No clarity)
def calc(w, h):
    return w * h

✅ GOOD: Professional Standard
def calculate_area(width: float, height: float) -> float:
    """Calculate rectangle area.
    
    Args:
        width: Rectangle width in units.
        height: Rectangle height in units.
    
    Returns:
        The area in square units.
    """
    return width * height
```

### Function Best Practices Checklist

| Practice | ✅ Do This | ❌ Never Do This |
|----------|-----------|---|
| **Naming** | `get_user_by_id()` | `func()`, `process_stuff()` |
| **Length** | Max 20 lines per function | 100+ line functions |
| **Arguments** | ≤ 3 arguments (ideally) | 7+ arguments (use dataclass) |
| **Type Hints** | Required on all functions | Omit type hints |
| **Docstrings** | Google or NumPy style | No documentation |
| **Return Values** | One type per function | Multiple conflicting types |

---

## 9. Pro Tip: Automate Your Standards 🤖

**Install a linter. TODAY. Not tomorrow.**

### The Two Essential Tools

#### 1. **Black** (Automatic Code Formatter)
```bash
pip install black
black your_file.py  # Formats everything automatically
```

**Why:** You never argue about spacing again. Ever.

#### 2. **Flake8** (Style & Error Checker)
```bash
pip install flake8
flake8 your_file.py  # Flags violations
```

**Why:** Catches PEP 8 violations before code review.

### Pre-Commit Hook Setup (One-Time Investment)

```bash
pip install pre-commit
cat > .pre-commit-config.yaml << 'EOF'
repos:
  - repo: https://github.com/psf/black
    rev: 23.1.0
    hooks:
      - id: black

  - repo: https://github.com/pycqa/flake8
    rev: 6.0.0
    hooks:
      - id: flake8
        args: [--max-line-length=100]
EOF

pre-commit install
```

**Result:** Every commit is automatically linted. Non-negotiable standards.

---

## Summary: The Trigger Standard 📋

| Pillar | Standard | Why It Matters |
|--------|----------|---|
| **PEP 8** | 4 spaces, 79 chars, proper imports | Pass code reviews, avoid chaos |
| **Environment Setup** | Virtual environments (.venv) | Project isolation, system safety |
| **Editor Config** | Auto-format, linting enabled | Catch errors before commit |
| **Naming** | snake_case, CapWords, ALL_CAPS | Team consistency, clarity |
| **References** | Understand mutable/immutable | Prevent subtle bugs |
| **Data Structures** | Master the Big 4 | 90% of problems solved |
| **Control Flow** | Guard clauses, no nesting | Readability = speed |
| **Loops** | Pythonic iteration | Clean, efficient code |
| **Functions** | Type hints + docstrings | Maintainable contracts |
| **Standards** | Automated linting (Black, Flake8) | No human judgment—just facts |

---

## What's Next?

You've absorbed the **prerequisites**. The foundation is set.

- 🎯 **01_Variables**: Deep dive into scope, lifetime, and memory.
- 🎯 **02_Data_Types**: Master strings, numbers, and sequences.
- 🎯 **03_Control_Structures**: Build bulletproof conditionals and loops.

---

**Last Word:** Write code for the person who reads it six months from now. That person is you, exhausted, at 2 AM, trying to fix a bug.

Make their life easy. Make your future self proud. 🏆
