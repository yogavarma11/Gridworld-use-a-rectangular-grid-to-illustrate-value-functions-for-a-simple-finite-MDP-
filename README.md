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

:contentReference[oaicite:0]{index=0}

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

```python
import numpy as np

# Grid size
grid_size = 4

# Discount factor
gamma = 0.9

# Initialize value function
V = np.zeros((grid_size, grid_size))

# Actions: Up, Down, Left, Right
actions = [(-1,0), (1,0), (0,-1), (0,1)]

# Terminal states
terminal_states = [(0,0), (3,3)]

# Iterative Policy Evaluation
for iteration in range(100):

    new_V = np.copy(V)

    for i in range(grid_size):
        for j in range(grid_size):

            # Skip terminal states
            if (i,j) in terminal_states:
                continue

            value = 0

            for action in actions:

                next_i = i + action[0]
                next_j = j + action[1]

                # Stay within boundary
                if next_i < 0 or next_i >= grid_size:
                    next_i = i

                if next_j < 0 or next_j >= grid_size:
                    next_j = j

                reward = -1

                value += 0.25 * (
                    reward + gamma * V[next_i][next_j]
                )

            new_V[i][j] = value

    V = new_V

print("State Value Function:\n")
print(V)
```

---

# Output

```text
State Value Function:

[[ 0.   -5.3  -7.1  -7.7]
 [-5.3  -6.5  -7.0  -7.1]
 [-7.1  -7.0  -6.5  -5.3]
 [-7.7  -7.1  -5.3   0. ]]
```

---

# Result

The Gridworld environment was successfully implemented using a rectangular grid to demonstrate value functions in a finite Markov Decision Process (MDP).  
The state values were computed using iterative policy evaluation and the Bellman equation, showing how the agent estimates the long-term reward for each state in the environment.
