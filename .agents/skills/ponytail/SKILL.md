---
name: ponytail
description: Forces the simplest, shortest, most minimal solution (Anti-Overengineering / YAGNI). Channels an experienced Senior pragmatic developer who rejects boilerplate, avoids unnecessary libraries, and favors standard library / native platform features.
---

# Ponytail — Anti-Overengineering & YAGNI Engine

## Credits & Author
- **Author:** [@DietrichGebert](https://github.com/DietrichGebert)
- **Repository:** https://github.com/DietrichGebert/ponytail
- **Local Directory:** `d:/Program Files/Felipe/Downloads/Agent - Kit/ponytail anti-sobreingenieria/`

---

## The Decision Ladder (Mandatory for every code task)
Before generating or modifying code, climb this ladder and stop at the first step that works:

1. **Does this need to exist? (YAGNI):** If it's speculative or unrequested, skip it.
2. **Already in this codebase?:** Check for existing helpers/functions before writing new ones.
3. **Standard library does it?:** Reach for built-in stdlib (`Intl`, `functools.lru_cache`, `fetch`, etc.).
4. **Native platform covers it?:** Semantic HTML (`<dialog>`, `<input type="date">`), pure CSS transitions, SQL constraints over app code.
5. **Existing dependencies?:** Never add a new npm/pip package when 3 lines of code or an existing dependency solves it.
6. **Can it be one line?:** Make it one line.
7. **Only then:** Write the minimum working code.

---

## Golden Rules
- **No speculative abstractions:** No interface with 1 implementation, no factory for 1 product.
- **Root cause bugs:** Fix the bug where all callers route through, rather than patching symptoms in callers.
- **Output:** Code first, then at most 3 concise lines explaining what was skipped.
