# Code Review Example Pack

---

## Purpose

These examples define the expected level of depth, reasoning quality, and evaluation rigor.

The assistant MUST align with these patterns.

---

## Example 1 — Fat Controller

### Scenario

Controller contains validation, business logic, and database operations.

---

### Weak Response

“Looks fine. Maybe refactor later.”

---

### Failure Analysis

* No structural evaluation
* No reasoning provided
* No actionable guidance

---

### Strong Response

“This implementation is functionally correct but introduces architectural issues.

Issues:

* Business logic is embedded in the controller (violates separation of concerns)
* Tight coupling between HTTP layer and business logic
* Reduced testability

Risks:

* Increased maintenance cost
* Difficult to reuse logic

Recommendation:

* Extract business logic into a service layer
* Keep controller focused on request handling

Architectural Impact:
This improves modularity, testability, and long-term maintainability.”

---

## Example 2 — Poor Naming

### Scenario

Variable named `data`

---

### Weak Response

“Rename this variable.”

---

### Failure Analysis

* No explanation
* No reasoning
* No architectural context

---

### Strong Response

“The variable name `data` is too generic and obscures intent.

Issue:

* Lack of semantic meaning

Risk:

* Increased cognitive load for future maintainers

Recommendation:
Rename to a descriptive term such as `userRegistrationPayload`

Architectural Impact:
Clear naming improves readability and reduces the need for code tracing.”

---

## Example 3 — Hidden Coupling

### Scenario

Service depends on internal structure of another service

---

### Weak Response

“This should work.”

---

### Failure Analysis

* No risk awareness
* No structural reasoning

---

### Strong Response

“This introduces hidden coupling.

Issue:

* Dependency relies on internal implementation rather than a defined interface

Risk:

* Changes in the dependent service may break this component

Recommendation:
Introduce an abstraction or interface to formalize the contract

Architectural Impact:
Reduces fragility and improves system stability.”
