# 🎯 Goal-Based Agent in Artificial Intelligence

### AI Vault | Chapter 07 — Goal-Based Agents & AI Planning

Welcome to the **Goal-Based Agent** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

A **Goal-Based Agent** is an intelligent agent that selects actions based on the goals it wants to achieve.

Unlike simple reflex agents that react to immediate conditions, goal-based agents consider **future states, possible actions, and whether those actions help achieve a desired objective**.

This makes them particularly useful for Artificial Intelligence applications involving planning, navigation, robotics, and automated problem solving.

This chapter explores goal-based agents through visual explanations, real-world examples, AI planning concepts, and a practical Python implementation.

---

## 🎨 Goal-Based Agent — Visual Explanation

<p align="center">
  <img src="./Goal-Based%20Agent_%20AI%20Planning%20Infographic.png"
       alt="Goal-Based Agent in Artificial Intelligence — Planning, Goals, Actions and Decision-Making"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: An illustrated overview of a Goal-Based Agent, demonstrating how an intelligent agent plans actions to reach a desired goal.</em>
</p>

The infographic illustrates how a goal-based agent uses information about its environment, evaluates possible future states, and selects actions that help it reach a specific goal.

---

## 🧠 What Is a Goal-Based Agent?

A **Goal-Based Agent** is an intelligent agent that makes decisions by considering whether its actions will lead to a desired goal state.

It typically uses:

1. **Current State:** Information about the environment.
2. **Goal State:** The desired outcome.
3. **Actions:** Operations available to the agent.
4. **Transition Model:** Knowledge of how actions change the environment.
5. **Search or Planning:** A method for finding actions that lead to the goal.

### Key Idea

**Current State + Goal + Available Actions + World Model → Plan → Action**

For example, a navigation system knows its current location and destination. It searches for a route and recommends actions that lead toward the destination.

### Key Characteristics

- 🎯 Works toward explicit goals.
- 🧠 Uses knowledge about the environment.
- 🔍 Considers possible future states.
- 🗺️ Can use search and planning algorithms.
- 🔄 Can revise plans when the environment changes.
- 🤖 Supports more flexible behavior than fixed condition–action rules.

## ⚙️ Architecture of a Goal-Based Agent

A goal-based agent combines environmental information with a goal to select actions.

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
        │     GOAL-BASED AGENT     │
        │                          │
        │   Update Current State   │
        │            ↓             │
        │   World / Action Model   │
        │            ↓             │
        │      Desired Goal        │
        │            ↓             │
        │    Search & Planning     │
        │            ↓             │
        │      Select Action       │
        └────────────┬─────────────┘
                     ↓
                ┌───────────┐
                │ Actuators │
                └─────┬─────┘
                      │
                    Action
                      ↓
        ┌──────────────────────────┐
        │       ENVIRONMENT        │
        └──────────────────────────┘
```

### Main Components

| Component | Description |
|---|---|
| Sensors | Receive information from the environment |
| Current State | Represents the agent's current situation |
| World Model | Describes how the environment changes |
| Goal | Defines the desired outcome |
| Actions | Operations available to the agent |
| Search / Planning | Identifies sequences of actions that can reach the goal |
| Actuators | Execute the selected actions |

## 🔄 How Does a Goal-Based Agent Work?

### Step 1: Perceive the Environment

The agent collects information through its sensors.

**Example:** A delivery robot determines its current position.

### Step 2: Identify the Goal

The agent identifies the state it wants to achieve.

**Example:** Deliver a package to Room D.

### Step 3: Generate Possible Actions

The agent identifies available actions.

**Example:** Move left, right, forward, or backward.

### Step 4: Predict Future States

Using its world model, the agent determines how available actions may change the environment.

**Example:** Moving through a corridor changes the robot's position.

### Step 5: Search for a Plan

The agent uses search or planning techniques to find a sequence of actions leading to the goal.

**Example:** Find a route from Room A to Room D.

### Step 6: Execute the Action

The agent executes an action from the selected plan.

### Step 7: Monitor and Replan

If the environment changes, the agent can update its state and calculate a new plan.

---

## 🗺️ Example: Goal-Based Navigation Agent

Consider an agent navigating between connected locations.

```text
       A ───── B ───── D
       │       │       │
       │       │       │
       C ───── E ───── F
```

**Initial State:** A

**Goal State:** D

The agent must identify a valid route from A to D.

Possible routes include:

- A → B → D
- A → C → E → B → D
- A → C → E → F → D

A search algorithm can identify a route that reaches the goal.

If each edge has equal cost, Breadth-First Search (BFS) can find a route using the fewest edges.

### Example Solution

**A → B → D**

The agent reaches its desired goal in two moves.

## 💻 Python Implementation

Let's implement a simple goal-based navigation agent using Breadth-First Search.

```python
from collections import deque


def goal_based_agent(graph, start, goal):
    """
    Find a shortest path in an unweighted graph
    using Breadth-First Search.
    """

    queue = deque([(start, [start])])
    visited = {start}

    while queue:
        current, path = queue.popleft()

        if current == goal:
            return path

        for neighbor in graph.get(current, []):
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(
                    (neighbor, path + [neighbor])
                )

    return None


graph = {
    "A": ["B", "C"],
    "B": ["A", "D", "E"],
    "C": ["A", "E"],
    "D": ["B", "F"],
    "E": ["B", "C", "F"],
    "F": ["D", "E"]
}

start = "A"
goal = "D"

path = goal_based_agent(graph, start, goal)

if path:
    print("Goal achieved!")
    print("Path:", " -> ".join(path))
else:
    print("No path found.")
```

### Expected Output

```text
Goal achieved!
Path: A -> B -> D
```

### Explanation

The agent:

1. Starts at location A.
2. Defines location D as the goal.
3. Explores connected locations using BFS.
4. Finds a valid path to the destination.
5. Returns the path.

This is a simplified planning example in a known, static environment. A physical robot would also need to execute actions, observe changes, and replan when necessary.

---

## 🔍 Search Algorithms Used by Goal-Based Agents

| Algorithm | Description | Typical Application |
|---|---|---|
| Breadth-First Search | Explores states level by level | Shortest path in unweighted graphs |
| Depth-First Search | Explores one branch before backtracking | State-space exploration |
| Uniform-Cost Search | Expands paths in increasing cost order | Lowest-cost pathfinding |
| Greedy Best-First Search | Uses a heuristic estimate to guide exploration | Fast heuristic search |
| A* Search | Combines path cost and estimated remaining cost | Optimal pathfinding with suitable heuristics |

Different algorithms offer different trade-offs in computational cost, memory usage, completeness, and optimality.

## 🌍 Real-World Applications

| Application | Goal |
|---|---|
| Autonomous Navigation | Reach a destination |
| Warehouse Robotics | Deliver items to specified locations |
| Game-Playing AI | Achieve a winning state |
| Automated Planning | Complete a sequence of tasks |
| Space Exploration | Reach a target location or perform a mission |
| Scheduling Systems | Complete tasks while satisfying constraints |
| Smart Assistants | Execute a sequence of steps to fulfill a request |

Goal-based reasoning may be combined with learning, optimization, and utility-based decision-making in real systems.

## ⚖️ Advantages and Limitations

### ✅ Advantages

- **Goal-Oriented Behavior:** Actions are selected to achieve objectives.
- **Planning Capability:** Can consider future states and action sequences.
- **Flexibility:** Can change behavior when goals change.
- **Problem-Solving Ability:** Suitable for navigation and planning problems.
- **Adaptability:** Can replan when new information becomes available.

### ❌ Limitations

- **Computational Complexity:** Searching large state spaces can be expensive.
- **Model Dependence:** Planning quality depends on the accuracy of the world model.
- **Uncertainty:** Unexpected changes may invalidate a plan.
- **Goal Definition:** Poorly defined goals can lead to undesirable behavior.
- **Limited Preference Handling:** Reaching a goal alone does not specify which successful outcome is most desirable.

## 🆚 Comparison with Other Intelligent Agents

| Feature | Simple Reflex | Model-Based Reflex | Goal-Based |
|---|---|---|---|
| Uses Current Percept | Yes | Yes | Yes |
| Maintains Internal State | No | Yes | Often |
| Uses World Model | No | Yes | Typically |
| Explicit Goal | No | Not required | Yes |
| Planning | No | Not necessarily | Yes |
| Considers Future States | No | Limited | Yes |
| Example | Basic thermostat | Obstacle-aware robot | Navigation agent |

### Key Difference

**Simple Reflex Agent:** "What should I do based on what I see now?"

**Model-Based Reflex Agent:** "What should I do based on my current understanding of the environment?"

**Goal-Based Agent:** "Which actions will help me reach my desired goal?"

## 📚 Learning Materials

This chapter includes two PDF resources and a visual infographic.

| Resource | Description |
|---|---|
| [📕 AI -13.pdf](AI%20-13.pdf) | Chapter learning material |
| [📕 AI -14.pdf](AI%20-14.pdf) | Additional chapter learning material |
| [🎨 Goal-Based Agent Infographic](Goal-Based%20Agent_%20AI%20Planning%20Infographic.png) | Illustrated overview of goal-based agents and planning |

Use the infographic to understand the overall architecture and the PDFs to explore the topic in greater detail.

## 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- [ ] Define a Goal-Based Agent.
- [ ] Explain the role of goals in intelligent decision-making.
- [ ] Identify the components of a goal-based architecture.
- [ ] Understand the relationship between search and planning.
- [ ] Explain how agents evaluate possible future states.
- [ ] Implement a basic goal-based navigation agent using Python.
- [ ] Compare goal-based agents with reflex-based agents.
- [ ] Identify practical applications and limitations.

## 💡 Key Takeaway

> A Goal-Based Agent does not simply react to the present. It considers what it wants to achieve and selects actions that can move it toward that goal.

Goal-based agents provide a foundation for AI planning, autonomous navigation, robotic decision-making, and intelligent problem solving.

---

## 🚀 Continue Learning

Explore more chapters in the [AI Vault](../), including utility-based agents, learning agents, and AI search algorithms.

### ⭐ Support This Project

If these visual explanations help you understand Artificial Intelligence, consider giving the [Primitive AI repository](https://github.com/ranjiGT/primitive-ai) a ⭐.

**Learn • Explore • Build • Share**

Made for curious minds and lifelong learners.
