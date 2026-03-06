---
name: testing-tdd
description: The Red-Green-Refactor Protocol. Zero-implementation without a failing test.
type: skill
id: testing-tdd
---

# Skill: TDD Protocol

**MANDATE:** No implementation without representation. If it isn't tested, it doesn't exist.
**TRIGGER:** `/sr:mission` (TDD Mode) or Critical Bug Fixes.

## 🔄 THE CYCLE (Red-Green-Refactor)

### 1. 🔴 RED (The Spec)
* **Action:** Write the test case *before* the function exists.
* **Verification:** Run the test.
* **Constraint:** It **MUST FAIL**.
    * If it passes, the test is broken or the feature already exists.
    * *Stop and investigate.*

### 2. 🟢 GREEN (The Implementation)
* **Action:** Write the *minimum amount of code* required to make the test pass.
* **Constraint:** Do not optimize yet. Do not over-engineer. Just make the bar turn green.
* **Verification:** Run the test. It **MUST PASS**.

### 3. 🔵 REFACTOR (The Polish)
* **Action:** Clean up the code.
    * Apply `skills/style-hemingway.md` (Terse, Early Returns).
    * Remove duplication (DRY).
    * Improve naming.
* **Constraint:** The test **MUST REMAIN GREEN**.

## 📏 TECHNICAL CONSTRAINTS

### 1. Math & Floats
* **Rule:** NEVER use strict equality (`toBe` / `===`) for floating point numbers.
* **Fix:** Use approximate equality (Epsilon check).
    * *JS/TS:* `expect(value).toBeCloseTo(expected, 5)`
    * *Rust:* `assert_abs_diff_eq!(a, b, epsilon = 1e-5)`
    * *C++ (gtest):* `EXPECT_NEAR(a, b, 1e-5)`
    * *Python (pytest):* `assert a == pytest.approx(b, abs=1e-5)`

### 2. External Dependencies (IO/Network)
* **Rule:** Unit tests MUST NOT hit the network or disk.
* **Fix:** **MOCK** all boundaries.
    * Database -> Mock Repository.
    * API -> Mock Client.
* *Why:* Tests must be fast (<10ms) and deterministic.

### 3. The Iceberg Principle (Testing)
* **Rule:** Test **Public Interfaces** (`export`), NOT private implementation details.
* **Goal:** Refactoring internals should NOT break tests.

## 📊 COVERAGE STANDARDS

| Area | Target | Strictness |
| :--- | :--- | :--- |
| **Critical Logic** (Auth, Money, Math) | **100%** | Absolute. Branch coverage required. |
| **Business Logic** (Features) | **80%** | Happy path + Common edge cases. |
| **UI Components** | **Smoke** | Does it render? Do buttons click? |
| **Utils** | **90%** | Pure functions must be bulletproof. |

## 🚫 ANTI-PATTERNS (Rejected by Critic)

1.  **The "Afterthought" Test:** Writing tests *after* the code is done. (This is not TDD).
2.  **The "Sleepy" Test:** Using `setTimeout` in tests. (Use proper async/await or fake timers).
3.  **The "Console" Test:** checking `console.log` output instead of assertions.
4.  **The "Happy Only" Test:** Testing only the success case. (You MUST test failure modes: 404s, invalid inputs).

## ✨ EXAMPLES

### ❌ Bad (Implementation Testing)
```typescript
// Testing private state - brittle!
test('user state', () => {
  const user = new User();
  user._internalState = 'active'; // Don't touch privates
  expect(user.calculateStatus()).toBe('active');
});

```

### ✅ Good (Behavior Testing)

```typescript
// Testing public behavior - robust
test('user activation', () => {
  // 1. Arrange
  const user = new User();
  // 2. Act
  user.activate();
  // 3. Assert (Public Interface)
  expect(user.isActive()).toBe(true);
});

```
