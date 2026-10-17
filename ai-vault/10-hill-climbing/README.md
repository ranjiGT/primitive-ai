# 🏔️ Hill Climbing Algorithm in Artificial Intelligence

### AI Vault | Chapter 10 — Local Search & Optimization Techniques

Welcome to the **Hill Climbing Algorithm** chapter of [Primitive AI](https://github.com/ranjiGT/primitive-ai)!

**Hill Climbing** is a local search algorithm used in Artificial Intelligence to find better solutions by repeatedly moving from the current state to a neighboring state with a higher evaluation value.

Imagine climbing a mountain in thick fog. You cannot see the entire mountain, but you can examine nearby positions and move uphill. Eventually, you may reach a peak where no neighboring position is higher.

This is the fundamental idea behind the Hill Climbing Algorithm.

This chapter explores hill climbing through visual explanations, mathematical concepts, practical examples, Python implementations, and common optimization challenges.

---

## 🎨 Hill Climbing — Visual Explanation

<p align="center">
  <img src="./Hill%20Climbing%20in%20AI%20Infographic.png"
       alt="Hill Climbing Algorithm in Artificial Intelligence — Local Search, Optimization, Local Maximum and Global Maximum"
       width="100%">
</p>

<p align="center">
  <em>Figure 1: An illustrated overview of the Hill Climbing Algorithm, showing how an agent searches for better solutions by moving uphill.</em>
</p>

The infographic helps visualize how hill climbing searches a landscape of possible solutions, improves its current position, and encounters challenges such as local maxima.

---

## 🧠 What Is Hill Climbing?

**Hill Climbing** is an iterative local search algorithm that attempts to improve a solution by examining neighboring states.

It starts with an initial solution and repeatedly moves to a better neighboring solution until no improvement is possible.

### Key Idea

**Initial State → Evaluate Neighbors → Choose Better State → Repeat → Local Optimum**

Hill climbing is commonly used for optimization problems where finding a good solution is more important than exploring every possible state.

### Key Characteristics

- 🔍 Uses local search rather than exhaustive search.
- 📈 Improves the current solution iteratively.
- 🧠 Uses an evaluation or objective function.
- ⚡ Often requires relatively little memory.
- 🎯 Can find good solutions efficiently.
- ⚠️ Does not guarantee finding the global optimum.

## ⚙️ How Does Hill Climbing Work?

### Step 1: Initialize a State

Choose a starting point in the search space.

**Example:** Start at position `x = 0`.

### Step 2: Evaluate the Current State

Calculate the objective function value.

**Example:** Evaluate `f(x)`.

### Step 3: Generate Neighboring States

Identify nearby possible solutions.

**Example:** Consider `x - 1` and `x + 1`.

### Step 4: Compare Neighboring States

Evaluate the neighboring solutions.

### Step 5: Move to a Better Neighbor

If a neighboring state has a better evaluation value, move to that state.

### Step 6: Repeat

Continue evaluating and moving to better states.

### Step 7: Terminate

Stop when no neighboring state provides an improvement.

The final state is a **local optimum with respect to the chosen neighborhood**, which may or may not be the global optimum.

---

## 🗺️ Hill Climbing Search Workflow

```mermaid
flowchart TD
    A([Start]) --> B[Choose Initial State]
    B --> C[Evaluate Current State]
    C --> D[Generate Neighboring States]
    D --> E[Evaluate Neighbors]
    E --> F{Better Neighbor Exists?}
    F -->|Yes| G[Move to Better Neighbor]
    G --> C
    F -->|No| H([Stop at Local Optimum])
```

### Basic Pseudocode

```text
HILL_CLIMBING(initial_state):

    current = initial_state

    LOOP:

        neighbor = BEST_NEIGHBOR(current)

        IF VALUE(neighbor) <= VALUE(current):
            RETURN current

        current = neighbor
```

This represents steepest-ascent hill climbing for a maximization problem.

For minimization problems, the comparison is reversed.

## 📈 Understanding the Search Landscape

Consider a landscape containing several peaks.

```text
Objective Value
      ^
      |
      |                         GLOBAL MAXIMUM
      |                              /\
      |                             /  \
      |          LOCAL MAXIMUM     /    \
      |              /\           /      \
      |             /  \         /        \
      |            /    \_______/          \
      |           /
      |     START
      |       ●
      |
      +----------------------------------------> State Space
```

The algorithm moves toward states with higher objective values.

However, if it reaches the smaller peak, it may stop because moving toward the larger peak would initially require moving downhill.

This is called the **local maximum problem**.

## 🧩 Types of Hill Climbing Algorithms

### 1. Simple Hill Climbing

Examines neighboring states sequentially and moves to the first state that improves the objective value.

**Advantages:** Easy to implement and often computationally inexpensive.

**Limitation:** The chosen improvement depends on neighbor examination order.

### 2. Steepest-Ascent Hill Climbing

Evaluates all immediate neighboring states and selects the one with the highest improvement.

**Advantages:** Makes the best locally available move according to the evaluation function.

**Limitation:** Evaluating every neighbor can be expensive.

### 3. Stochastic Hill Climbing

Randomly selects among improving neighboring states, potentially using a probability distribution.

**Advantages:** Introduces randomness into the search.

**Limitation:** May require additional iterations and does not guarantee a global optimum.

### 4. First-Choice Hill Climbing

Generates neighboring states randomly until it finds one that improves the current state.

**Advantages:** Useful when the neighborhood is extremely large.

**Limitation:** May spend time searching for an improving neighbor when improvements are rare.

### 5. Random-Restart Hill Climbing

Runs hill climbing multiple times from different randomly selected initial states.

**Advantages:** Improves the chance of finding a better optimum.

**Limitation:** Requires additional computational effort.

## ⚠️ Common Problems in Hill Climbing

### 🏔️ Local Maximum

A local maximum is a state better than its neighboring states but not necessarily the best state in the entire search space.

**Problem:** The algorithm stops even though a better solution exists elsewhere.

**Possible Solution:** Random-restart hill climbing.

### 🟰 Plateau

A plateau is a region where neighboring states have equal or nearly equal evaluation values.

**Problem:** The algorithm cannot identify a strictly improving direction.

**Possible Solution:** Allow limited sideways moves or restart from another state.

### ⛰️ Ridge

A ridge is a narrow region of high evaluation values where the available moves may not align with the direction of improvement.

**Problem:** The algorithm may struggle to follow the ridge using its current neighborhood definition.

**Possible Solution:** Use a richer neighborhood, alternative move operators, or randomized search.

### 🔄 Shoulder

A shoulder is a flat region that may eventually lead to an improvement.

**Problem:** A strictly improving algorithm may terminate before crossing it.

**Possible Solution:** Permit a bounded number of sideways moves.

## 💻 Python Implementation

Let's implement **Steepest-Ascent Hill Climbing** using a simple mathematical objective function.

We want to maximize:

`f(x) = -(x - 5)² + 25`

This function has its global maximum at `x = 5`, where `f(x) = 25`.

```python
def objective_function(x):
    return -(x - 5) ** 2 + 25


def hill_climbing(start, step_size=1):
    current = start

    while True:
        neighbors = [
            current - step_size,
            current + step_size
        ]

        best_neighbor = max(
            neighbors,
            key=objective_function
        )

        if objective_function(best_neighbor) <= objective_function(current):
            break

        current = best_neighbor

        print(
            f"x = {current}, "
            f"f(x) = {objective_function(current)}"
        )

    return current


best_solution = hill_climbing(start=0)

print("\nBest Solution:", best_solution)
print("Maximum Value:", objective_function(best_solution))
```

### Expected Output

```text
x = 1, f(x) = 9
x = 2, f(x) = 16
x = 3, f(x) = 21
x = 4, f(x) = 24
x = 5, f(x) = 25

Best Solution: 5
Maximum Value: 25
```

### Explanation

The algorithm starts at `x = 0` and examines two neighboring states at every iteration.

It moves toward states with higher objective values until it reaches `x = 5`.

At this point, both neighboring states have lower objective values, so the algorithm terminates.

**Note:** The example is deliberately simple. The global maximum is known mathematically, but a general hill climbing algorithm cannot guarantee finding the global maximum for an arbitrary objective function.

---

## 🎲 Random-Restart Hill Climbing

One technique for overcoming local maxima is to run hill climbing from multiple starting points.

```python
import random


def random_restart_hill_climbing(
    objective,
    lower_bound,
    upper_bound,
    restarts=20
):
    def climb(start):
        current = start

        while True:
            neighbors = [
                x for x in (current - 1, current + 1)
                if lower_bound <= x <= upper_bound
            ]

            better = [
                x for x in neighbors
                if objective(x) > objective(current)
            ]

            if not better:
                return current

            current = max(better, key=objective)

    best_solution = None

    for _ in range(restarts):
        start = random.randint(
            lower_bound,
            upper_bound
        )

        solution = climb(start)

        if (
            best_solution is None
            or objective(solution) > objective(best_solution)
        ):
            best_solution = solution

    return best_solution


result = random_restart_hill_climbing(
    objective=objective_function,
    lower_bound=-10,
    upper_bound=10,
    restarts=20
)

print("Best Solution:", result)
print("Best Value:", objective_function(result))
```

Random restarts increase the chance of discovering a better solution when the search landscape contains multiple local optima.

They do not guarantee a global optimum with a finite number of runs.

## 🌍 Real-World Applications

| Application | Role of Hill Climbing |
|---|---|
| Feature Selection | Search for useful feature subsets |
| Hyperparameter Optimization | Improve model configurations |
| Job Scheduling | Improve task assignments |
| Route Optimization | Improve candidate routes |
| Timetabling | Reduce scheduling conflicts |
| Resource Allocation | Improve resource assignments |
| Game AI | Improve evaluation-based decisions |
| Engineering Design | Optimize design parameters |

The effectiveness of hill climbing depends heavily on the objective function, neighborhood definition, and search landscape.

## ⚖️ Advantages and Limitations

### ✅ Advantages

- **Simple Implementation:** Easy to understand and implement.
- **Memory Efficient:** Usually stores only the current state and nearby candidates.
- **Fast Local Improvement:** Often discovers better solutions quickly.
- **Flexible:** Can be adapted to many optimization problems.
- **Scalable Variants:** Randomized approaches can help with large neighborhoods.

### ❌ Limitations

- **Local Optima:** May stop before finding the global optimum.
- **Plateaus:** Equal-valued neighboring states can prevent progress.
- **Ridges:** Some search landscapes are difficult to navigate.
- **Starting-Point Sensitivity:** Results may depend on the initial state.
- **No General Optimality Guarantee:** A locally optimal solution may be far from globally optimal.

## 🆚 Hill Climbing vs. Other Search Algorithms

| Feature | Hill Climbing | BFS | A* Search |
|---|---|---|---|
| Search Type | Local optimization | Graph search | Heuristic graph search |
| Main Objective | Improve evaluation value | Find a path | Find a low-cost path |
| Memory Usage | Often low | Potentially high | Potentially high |
| Uses Heuristic/Evaluation | Yes | No | Yes |
| Global Optimality | Not guaranteed | Shortest path in unweighted graphs | Under suitable conditions |
| Common Application | Optimization | Pathfinding | Pathfinding |

Hill climbing is primarily used for optimization, whereas BFS and A* are commonly used to find paths through state spaces.

## 📚 Learning Materials

This chapter includes two PDF resources and an illustrated infographic.

| Resource | Description |
|---|---|
| [📕 AI -18.pdf](AI%20-18.pdf) | Chapter learning material |
| [📕 AI -19.pdf](AI%20-19.pdf) | Additional chapter learning material |
| [🎨 Hill Climbing Infographic](Hill%20Climbing%20in%20AI%20Infographic.png) | Illustrated explanation of hill climbing and its challenges |

Use the infographic as a visual reference while exploring the PDF learning materials.

## 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- [ ] Define the Hill Climbing Algorithm.
- [ ] Explain how local search works.
- [ ] Describe the role of an evaluation function.
- [ ] Differentiate between local and global maxima.
- [ ] Explain plateaus, ridges, and shoulders.
- [ ] Compare different hill climbing variants.
- [ ] Implement steepest-ascent hill climbing in Python.
- [ ] Explain random-restart hill climbing.
- [ ] Identify applications and limitations of hill climbing.

## 💡 Key Takeaway

> Hill Climbing is a local search technique that improves a solution step by step by moving toward better neighboring states. It is simple and efficient, but it can become trapped in local optima.

Understanding hill climbing provides a foundation for more advanced optimization methods, including simulated annealing, evolutionary algorithms, and metaheuristic search.

---

## 🚀 Continue Learning

Explore more chapters in the [AI Vault](../), including Cryptarithmetic Problems, intelligent agents, and AI problem-solving techniques.

### ⭐ Support This Project

If these visual explanations help you understand Artificial Intelligence, consider giving the [Primitive AI repository](https://github.com/ranjiGT/primitive-ai) a ⭐.

**Learn • Explore • Build • Share**

Made for curious minds and lifelong learners.
