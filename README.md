# Gridworld-use-a-rectangular-grid-to-illustrate-value-functions-for-a-simple-finite-MDP-

## Aim
The aim of this project is to implement a Gridworld environment using Reinforcement Learning concepts to illustrate value functions in a simple finite Markov Decision Process (MDP).

---

# Algorithm

## Iterative Policy Evaluation Algorithm for Gridworld

### Step 1
Initialize the Gridworld environment.

### Step 2
Define:
- States
- Actions
- Rewards
- Transition probabilities

### Step 3
Initialize the value function \( V(s) \) for all states to zero.

### Step 4
For each state:
- Evaluate all possible actions
- Compute the expected return

### Step 5
Update the state value using the Bellman Equation:

Where:
- \( \pi(a|s) \) → Policy
- \( \gamma \) → Discount factor
- \( r \) → Reward
- \( V(s') \) → Next state value

### Step 6
Repeat updates until the value function converges.

### Step 7
Display the final state-value grid.

---

# Program

```
```

---

# Output

```text
State Value Function:


```

---

# Result

The Gridworld environment was successfully implemented using a rectangular grid to demonstrate value functions in a finite Markov Decision Process (MDP).  
The state values were computed using iterative policy evaluation and the Bellman equation, showing how the agent estimates the long-term reward for each state in the environment.
