# 🧠 Model-Based Reflex Agent in Artificial Intelligence

### AI Vault | Chapter 06 — Model-Based Agent Architecture

Welcome to the **Model-Based Reflex Agent** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

A **Model-Based Reflex Agent** is an intelligent agent that maintains an **internal representation of its environment** to make decisions.

Unlike a Simple Reflex Agent, which responds only to its current percept, a Model-Based Reflex Agent uses both current observations and stored information about the environment.

This makes it particularly useful in **partially observable environments**, where an agent cannot see everything happening around it.

This chapter explores model-based agents through visual explanations, architecture diagrams, real-world examples, and a practical Python implementation.

---

## 🎨 Model-Based Agent — Visual Explanation

<p align="center">
  <img src="./Model-Based%20Agent%20Infographic.png"
       alt="Model-Based Agent in AI — Architecture, Internal State, World Model and Examples"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: An illustrated overview of a Model-Based Agent, showing how observations, internal state, and decision-making interact.</em>
</p>

The infographic demonstrates how an intelligent agent maintains an internal representation of its environment and updates that representation as new information becomes available.

---

## 🧠 What Is a Model-Based Reflex Agent?

A **Model-Based Reflex Agent** selects actions using:

1. The current percept received from the environment.
2. An internal state representing relevant aspects of the environment.
3. A model describing how the environment changes.
4. Condition–action rules used to select actions.

### Key Idea

**Current Percept + Previous Internal State + World Model → Updated State → Action**

For example, a robot navigating a building may remember the location of an obstacle even after the obstacle is no longer visible.

This ability allows the robot to make more informed decisions than an agent that considers only its immediate sensor readings.

## ⚙️ Architecture of a Model-Based Reflex Agent

A model-based agent maintains and updates an internal state before selecting an action.

```text
           ┌────────────────────────┐
           │      ENVIRONMENT       │
           └────────────┬───────────┘
                        │
                     Percept
                        ↓
                  ┌──────────┐
                  │ Sensors  │
                  └────┬─────┘
                       ↓
       ┌────────────────────────────┐
       │  MODEL-BASED REFLEX AGENT  │
       │                            │
       │  Current Percept           │
       │         ↓                  │
       │  Update Internal State ←──┐│
       │         ↓               │  │
       │  Internal World Model   │  │
       │         ↓               │  │
       │  Condition–Action Rules │  │
       │         ↓               │  │
       │  Select Action          │  │
       │         └───────────────┘  │
       └────────────┬───────────────┘
                    ↓
               ┌───────────┐
               │ Actuators │
               └─────┬─────┘
                     │
                   Action
                     ↓
           ┌────────────────────────┐
           │      ENVIRONMENT       │
           └────────────────────────┘
```

The internal state is updated using the previous state, previous action, current percept, and knowledge of how the environment changes.

### Main Components

| Component | Description |
|---|---|
| Sensors | Receive observations from the environment |
| Current Percept | Latest information detected by sensors |
| Internal State | Stores relevant information about the environment |
| World Model | Describes how the environment evolves and how actions affect it |
| State Update Function | Updates the internal state using new observations |
| Condition–Action Rules | Determine actions from the updated state |
| Actuators | Execute the selected actions |

## 🔄 How Does a Model-Based Agent Work?

### Step 1: Perceive the Environment

The agent receives information through its sensors.

**Example:** A robot detects an obstacle directly ahead.

### Step 2: Update the Internal State

The agent updates its internal representation of the environment.

**Example:** The robot records that the forward path is blocked.

### Step 3: Use the World Model

The agent considers how the environment changes and how its actions affect it.

**Example:** Moving backward changes the robot's position but does not necessarily remove the obstacle.

### Step 4: Apply Condition–Action Rules

The agent evaluates its updated internal state.

```text
IF obstacle_ahead = True
THEN turn_right

IF obstacle_ahead = False
THEN move_forward
```

### Step 5: Execute the Action

The selected action is executed through the agent's actuators.

### Step 6: Repeat

The agent observes the environment again and updates its internal state.

This continuous process allows the agent to maintain information across multiple observations.

---

## 🤖 Example: Robot with Obstacle Memory

Consider a robot moving through a corridor.

A Simple Reflex Agent responds only to the obstacle currently detected.

A Model-Based Reflex Agent can additionally remember previously observed obstacles.

### Example Scenario

| Step | Current Observation | Internal State | Action |
|---|---|---|---|
| 1 | Path ahead clear
