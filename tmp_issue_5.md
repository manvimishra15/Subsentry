**Expanded Description:**
This issue focuses on improving code quality early by removing hardcoded strings and values related to subscription categories and billing cycles.

Contributors will centralize these values into constants or enums so they can be reused consistently across frontend and backend.

**Why this issue exists:**
- Prevents bugs caused by mismatched strings
- Makes future features easier to add
- Encourages clean architecture practices

**Key Expectations:**
- Single source of truth for constants
- Used wherever applicable

**What NOT to do:**
- Duplicate constants across files
- Keep magic strings in components or controllers

---
