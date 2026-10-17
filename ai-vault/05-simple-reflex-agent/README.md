# 🤖 Simple Reflex Agent in Artificial Intelligence

### AI Vault | Chapter 05 — Simple Reflex Agent Architecture

Welcome to the **Simple Reflex Agent** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

A **Simple Reflex Agent** is one of the most fundamental types of intelligent agents in Artificial Intelligence. It makes decisions based entirely on the **current percept**, using predefined condition–action rules.

Unlike more advanced agents, a simple reflex agent does not maintain an internal model of the environment, plan for future outcomes, or learn from previous experiences.

This chapter explores its architecture, working principles, practical examples, advantages, and limitations through a visual infographic and structured learning materials.

---

## 🎨 Simple Reflex Agent — Visual Explanation

<p align="center">
  <img src="./Simple%20Reflex%20Agent%20Infographic.png"
       alt="Simple Reflex Agent in AI — Architecture, Working Principle and Examples"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: An illustrated overview of the Simple Reflex Agent, its condition–action rules, and its interaction with the environment.</em>
</p>

The infographic demonstrates how an agent receives information from its environment and immediately selects an action using predefined rules.

---

## 🧠 What Is a Simple Reflex Agent?

A **Simple Reflex Agent** is an intelligent agent that selects an action based only on the current percept.

It operates using **condition–action rules**, commonly expressed as:

**IF condition THEN action**

For example:

```text
IF temperature < 20°C
THEN turn on the heater

IF temperature >= 20°C
THEN turn off the heater
```

The agent does not need to remember previous temperature readings. It simply responds to the current sensor input.

### Key Characteristics

- ⚡ Responds directly to current percepts.
- 📋 Uses predefined condition–action rules.
- 🧠 Does not maintain an internal environment model.
- 🚀 Requires relatively little computation.
- 🔄 Performs the same action for the same percept under a fixed rule set.
- 🌍 Works best in simple, sufficiently observable environments.

## ⚙️ Architecture of a Simple Reflex Agent

The basic architecture follows a perception–action cycle.

```text
        ┌─────────────────────────┐
        │       ENVIRONMENT       │
        └────────────┬────────────┘
                     │
                  Percept
                     ↓
              ┌─────────────┐
              │   SENSORS   │
              └──────┬──────┘
                     ↓
        ┌─────────────────────────┐
        │   SIMPLE REFLEX AGENT   │
        │                         │
        │  Current Percept        │
        │          ↓              │
        │  Condition–Action Rules │
        │          ↓              │
        │  Selected Action        │
        └────────────┬────────────┘
                     ↓
              ┌─────────────┐
              │  ACTUATORS  │
              └──────┬──────┘
                     │
                   Action
                     ↓
        ┌─────────────────────────┐
        │       ENVIRONMENT       │
        └─────────────────────────┘
```

### Main Components

| Component | Description | Example |
|---|---|---|
| Environment | World in which the agent operates | Room |
| Sensors | Detect information from the environment | Dirt
