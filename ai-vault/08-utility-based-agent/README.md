# ⚖️ Utility-Based Agent in Artificial Intelligence

### AI Vault | Chapter 08 — Utility Functions & Intelligent Decision-Making

Welcome to the **Utility-Based Agent** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

A **Utility-Based Agent** is an intelligent agent that selects actions based on how desirable their expected outcomes are.

Unlike a Goal-Based Agent, which focuses on achieving a specific goal, a Utility-Based Agent evaluates different possible outcomes and chooses actions that maximize a defined **utility function**.

This makes utility-based agents particularly useful when multiple solutions exist, trade-offs must be considered, or decisions involve uncertainty.

This chapter explores utility-based agents through visual explanations, mathematical concepts, real-world examples, and a practical Python implementation.

---

## 🎨 Utility-Based Agent — Visual Explanation

<p align="center">
  <img src="./Utility-Based%20Agent%20Infographic.png"
       alt="Utility-Based Agent in Artificial Intelligence — Utility Functions, Decision-Making and Optimization"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: An illustrated overview of a Utility-Based Agent, showing how it evaluates possible outcomes and selects desirable actions.</em>
</p>

The infographic demonstrates how a utility-based agent compares alternatives using a utility function and chooses an action based on expected performance.

---

## 🧠 What Is a Utility-Based Agent?

A **Utility-Based Agent** is an intelligent agent that uses a utility function to evaluate the desirability of different outcomes.

A utility function assigns a numerical value to an outcome or state.

**Utility Function:**

`U(s) → Real Number`

Where:

- `U` = Utility function.
- `s` = A possible state or outcome.
- `U(s)` = Numerical desirability of that state.

A higher utility value indicates a more preferred outcome according to the agent's defined preferences.

### Key Idea

**Current State + Possible Actions + Predicted Outcomes + Utility Function → Best Action**

For example, a navigation system may evaluate multiple routes based on travel time, cost, distance, and safety.

Instead of choosing any route that reaches the destination, it selects a route that best satisfies its preferences.

## ⚙️ Architecture of a Utility-Based Agent

A utility-based agent evaluates possible outcomes before selecting an action.

```text
        ┌──────────────────────────┐
        │       ENVIRONMENT        │
        └────────────┬─────────────┘
                     │
                   Percept
                     ↓
                ┌─────────┐
                │ Sensors │
                └────┬────┘
                     ↓
        ┌──────────────────────────┐
        │    UTILITY-BASED AGENT   │
        │                          │
        │   Update Current State   │
        │            ↓             │
        │   Predict Outcomes       │
        │            ↓             │
        │   Evaluate Utilities     │
        │            ↓             │
        │   Compare Alternatives   │
        │            ↓             │
        │   Select Best Action     │
        └────────────┬─────────────┘
                     ↓
                ┌───────────┐
                │ Actuators │
                └─────┬─────
