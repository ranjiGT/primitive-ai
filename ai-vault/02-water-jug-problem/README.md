# 🪣 Water Jug Problem in Artificial Intelligence

### AI Vault | Chapter 02 — Problem Solving & State Space Search

Welcome to the **Water Jug Problem** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

The Water Jug Problem is a classic example in Artificial Intelligence used to demonstrate **state-space representation, problem formulation, search algorithms, and goal-based problem solving**.

The challenge is simple: given two water jugs with fixed capacities, can we measure an exact quantity of water using only a few permitted operations?

Let's explore the problem visually!

---

## 🎨 Water Jug Problem — Visual Explanation

<p align="center">
  <img src="./Water%20Jug%20Problem_%20AI%20Solution%20Path.png"
       alt="Water Jug Problem in AI — Step-by-Step Solution and State Space Search"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: Illustrated solution to the Water Jug Problem using state-space search.</em>
</p>

The infographic demonstrates how an AI problem-solving agent moves from an initial state to a goal state by applying valid operations.

## 🎯 Problem Statement

Suppose we have two jugs:

- 🪣 **Jug A:** Capacity of 5 liters
- 🪣 **Jug B:** Capacity of 3 liters

**Objective:** Measure exactly **4 liters** of water in Jug A.

### Conditions

- Both jugs are initially empty.
- An unlimited water supply is available.
- Jugs have no intermediate measurement markings.
- Water can be filled, emptied, or transferred between jugs.
- Neither jug can exceed its capacity.

## 🧠 State Space Representation

In Artificial Intelligence, a problem can be represented using states and transitions.

Let:

`(x, y)`

Where:

- `x` = Amount of water in the 5-liter jug.
- `y` = Amount of water in the 3-liter jug.

The valid state constraints are:

`0 ≤ x ≤ 5`

`0 ≤ y ≤ 3`

**Initial State:** `(0, 0)`

**Goal State:** `(4, 0)`

Each valid operation transforms one state into another.

## ⚙️ Allowed Operations

| Operation | Description |
|---|---|
| Fill Jug A | Fill the 5-liter jug completely |
| Fill Jug B | Fill the 3-liter jug completely |
| Empty Jug A | Empty the 5-liter jug |
| Empty Jug B | Empty the 3-liter jug |
| Pour A → B | Transfer water until A is empty or B is full |
| Pour B → A | Transfer water until B is empty or A is full |

These operations define the possible transitions between states.

## 🚀 Step-by-Step Solution

Let's solve the problem using a sequence of valid operations.

| Step | Operation | State (A, B) |
|---|---|---|
| 0 | Both jugs empty | `(0, 0)` |
| 1 | Fill the 5L jug | `(5, 0)` |
| 2 | Pour from 5L into 3L | `(2, 3)` |
| 3 | Empty the 3L jug | `(2, 0)` |
| 4 | Transfer remaining 2L into 3L | `(0, 2)` |
| 5 | Fill the 5L jug again | `(5, 2)` |
| 6 | Pour from 5L into 3L until full | `(4, 3)` |
| 7 | Empty the 3L jug | `(4, 0)` |

### ✅ Goal Achieved!

The final state is `(4, 0)`, meaning the 5-liter jug contains exactly 4 liters of water.

### Solution Path

```text
(0,0)
  ↓ Fill A
(5,0)
  ↓ Pour A → B
(2,3)
  ↓ Empty B
(2,0)
  ↓ Pour A → B
(0,2)
  ↓ Fill A
(5,2)
  ↓ Pour A → B
(4,3)
  ↓ Empty B
(4,0) 🎯 GOAL
```

## 🔍 How Does AI Solve This Problem?

AI search algorithms explore possible states to find a valid sequence of actions leading to the goal.

### Breadth-First Search (BFS)

BFS explores states level by level.

- Starts from the initial state.
- Generates all valid neighboring states.
- Avoids revisiting previously explored states.
- Continues until the goal is found.
- Finds a solution with the fewest operations when each action has equal cost.

### Depth-First Search (DFS)

DFS explores one path as deeply as possible before backtracking.

- Uses a stack or recursion.
- Explores one branch at a time.
- Can use a visited-state set to prevent cycles.
- Does not guarantee the shortest solution.

## 🧩 AI Concepts Demonstrated

| Concept | Application |
|---|---|
| Problem formulation | Define initial state, goal, and operations |
| State space | All valid water configurations |
| State transition | Moving between configurations |
| Goal testing | Check whether the required quantity is reached |
| Search algorithms | BFS and DFS explore possible solutions |
| Path finding | Discover a sequence of valid operations |

## 📚 Learning Resources

The following PDF materials accompany this chapter:

| Resource | Description |
|---|---|
| [📕 AI -3.pdf](AI%20-3.pdf) | Water Jug Problem learning notes |
| [📕 AI -4.pdf](AI%20-4.pdf) | Additional chapter learning material |
| [🎨 Visual Solution Diagram](Water%20Jug%20Problem_%20AI%20Solution%20Path.png) | Illustrated overview of the problem |

## 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- [ ] Explain the Water Jug Problem.
- [ ] Represent a problem using states.
- [ ] Identify initial and goal states.
- [ ] Define valid state-transition operations.
- [ ] Solve the Water Jug Problem step by step.
- [ ] Understand how BFS and DFS approach the problem.
- [ ] Recognize the role of search in AI problem solving.

## 💡 Key Takeaway

> Artificial Intelligence problem solving is about representing a problem clearly, defining valid actions, and systematically searching for a path from the initial state to the desired goal.

The Water Jug Problem illustrates how even a simple puzzle can demonstrate important principles of intelligent search.

---

## 🚀 Continue Learning

Explore more chapters in the [AI Vault](../) to learn about intelligent agents, search algorithms, optimization, and other fundamental AI concepts.

### ⭐ Support This Project

If this visual explanation helped you understand AI problem solving, consider giving the [Primitive AI repository](https://github.com/ranjiGT/primitive-ai) a ⭐.

**Learn • Explore • Build • Share**

Made for curious minds and lifelong learners.
