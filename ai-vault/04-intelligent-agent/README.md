# 🤖 Intelligent Agents in Artificial Intelligence

### AI Vault | Chapter 04 — Intelligent Agents & Agent Architectures

Welcome to the **Intelligent Agents** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

An intelligent agent is one of the fundamental concepts in Artificial Intelligence. It is a system that **perceives its environment, processes information, and takes actions to achieve specific objectives**.

From autonomous vehicles and robotic vacuum cleaners to virtual assistants and recommendation systems, intelligent agents form the foundation of many modern AI applications.

This chapter introduces intelligent agents through visual explanations, real-world examples, agent architectures, and structured learning resources.

---

## 🎨 Intelligent Agent — Visual Explanation

<p align="center">
  <img src="./Intelligent%20Agent%20in%20AI%20Infographic.png"
       alt="Intelligent Agent in AI — Architecture, Sensors, Actuators and Types"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: An illustrated overview of intelligent agents, their architecture, and their interaction with the environment.</em>
</p>

The infographic demonstrates how an intelligent agent receives information through sensors, processes percepts using its agent program, and performs actions through actuators.

---

## 🧠 What Is an Intelligent Agent?

An **intelligent agent** is an autonomous or semi-autonomous system that perceives its environment and selects actions to achieve its objectives.

An agent can be represented conceptually as:

**Agent = Architecture + Agent Program**

Where:

- **Architecture:** The hardware or software platform on which the agent operates.
- **Agent Program:** The implementation that processes percepts and determines actions.

An agent's behavior can also be described by an agent function:

`f: P* → A`

Where:

- `P*` = Set of all possible percept sequences.
- `A` = Set of available actions.
- `f` = Mapping from percept histories to actions.

### Example: Robotic Vacuum Cleaner

A robotic vacuum cleaner:

1. Detects dirt and obstacles.
2. Processes information from its sensors.
3. Determines where to move next.
4. Activates motors and cleaning mechanisms.
5. Continues operating as its environment changes.

This illustrates the basic perception–action cycle of an intelligent agent.

## ⚙️ Architecture of an Intelligent Agent

An intelligent agent interacts continuously with its environment.

```text
        ┌──────────────────────────┐
        │       ENVIRONMENT        │
        └────────────┬─────────────┘
                     │
                  Percepts
                     ↓
               ┌──────────┐
               │ Sensors  │
               └────┬─────┘
                    ↓
        ┌──────────────────────────┐
        │     INTELLIGENT AGENT    │
        │                          │
        │   Perception             │
        │       ↓                  │
        │   Decision Making        │
        │       ↓                  │
        │   Action Selection       │
        └────────────┬─────────────┘
                     ↓
               ┌──────────┐
               │Actuators │
               └────┬─────┘
                    │
                  Actions
                     ↓
        ┌──────────────────────────┐
        │       ENVIRONMENT        │
        └──────────────────────────┘
```

### Main Components

| Component | Description | Example |
|---|---|---|
| Environment | World in which the agent operates | Road, room, game |
| Sensors | Receive information from the environment | Camera, microphone, GPS |
| Percepts | Information received by the agent | Object detected, temperature |
| Agent Program | Determines actions based on percepts | Navigation algorithm |
| Actuators | Execute selected actions | Motors, robotic arms |
| Actions | Operations performed by the agent | Move, turn, stop |

For software agents, sensors and actuators can be logical interfaces such as API inputs and outputs.

## 🎯 Rational Intelligent Agents

A **rational agent** selects actions expected to maximize its performance measure based on the information available to it.

Rationality depends on:

- The performance measure.
- The agent's percept sequence.
- Its prior knowledge of the environment.
- The actions available to the agent.

**Important:** Rationality does not mean that an agent is always correct or knows everything. It means selecting the best expected action given the available information.

## 🧩 PEAS Framework

The PEAS framework is used to describe an intelligent agent's task environment.

**PEAS = Performance Measure, Environment, Actuators, Sensors**

### Example: Self-Driving Car

| PEAS Component | Description |
|---|---|
| Performance Measure | Safety, travel time, passenger comfort, legal compliance |
| Environment | Roads, pedestrians, traffic signals, other vehicles |
| Actuators | Steering, brakes, accelerator, indicators |
| Sensors | Cameras, radar, GPS, lidar |

PEAS helps AI developers define what an agent should achieve and how it interacts with its environment.

## 🌍 Types of Task Environments

Intelligent agents may operate in different types of environments.

| Environment Property | Categories |
|---|---|
| Observability | Fully observable / Partially observable |
| Determinism | Deterministic / Stochastic |
| Episodic Nature | Episodic / Sequential |
| Dynamics | Static / Dynamic |
| State Space | Discrete / Continuous |
| Number of Agents | Single-agent / Multi-agent |
| Knowledge | Known / Unknown |

For example, autonomous driving typically involves a partially observable, stochastic, dynamic, sequential, multi-agent environment.

## 🤖 Types of Intelligent Agents

Intelligent agents can be categorized according to how they make decisions.

### 1. Simple Reflex Agent

Responds directly to the current percept using predefined condition–action rules.

**Example:** A thermostat that switches heating on when the temperature falls below a threshold.

### 2. Model-Based Reflex Agent

Maintains an internal state representing aspects of the environment that may not be directly observable.

**Example:** A robot that remembers previously detected obstacles.

### 3. Goal-Based Agent

Selects actions based on whether they help achieve a desired goal.

**Example:** A
