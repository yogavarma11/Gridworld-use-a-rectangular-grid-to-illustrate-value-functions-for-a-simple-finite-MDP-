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
import numpy as np

# Grid size (rectangular)
rows, cols = 4, 5

gamma = 0.9      # discount factor
theta = 1e-4     # convergence threshold

# Rewards
rewards = np.zeros((rows, cols))
rewards[0, 4] = 1     # Goal
rewards[1, 4] = -1    # Bad state

# Actions: Up, Down, Left, Right
actions = [(-1,0), (1,0), (0,-1), (0,1)]
action_symbols = ["↑", "↓", "←", "→"]

# Initialize Value Function
V = np.zeros((rows, cols))

def is_valid(r, c):
    return 0 <= r < rows and 0 <= c < cols

# --- VALUE ITERATION ---
while True:
    delta = 0
    new_V = np.copy(V)

    for r in range(rows):
        for c in range(cols):
            values = []

            for a in actions:
                nr, nc = r + a[0], c + a[1]

                if not is_valid(nr, nc):
                    nr, nc = r, c   # stay in same cell

                reward = rewards[nr, nc]
                values.append(reward + gamma * V[nr, nc])

            best_value = max(values)
            new_V[r, c] = best_value

            delta = max(delta, abs(V[r, c] - best_value))

    V = new_V

    if delta < theta:
        break

# --- PRINT VALUE FUNCTION ---
print("\nValue Function:\n")
for row in V:
    print(["{0:0.2f}".format(v) for v in row])


# --- EXTRACT POLICY ---
policy = np.empty((rows, cols), dtype=str)

for r in range(rows):
    for c in range(cols):
        action_values = []

        for a in actions:
            nr, nc = r + a[0], c + a[1]

            if not is_valid(nr, nc):
                nr, nc = r, c

            reward = rewards[nr, nc]
            action_values.append(reward + gamma * V[nr, nc])

        best_action = np.argmax(action_values)
        policy[r, c] = action_symbols[best_action]

# --- PRINT POLICY ---
print("\nPolicy:\n")
for row in policy:
    print(row)

```

# Output

<img width="428" height="279" alt="image" src="https://github.com/user-attachments/assets/a9e9d3c8-94f1-4275-906b-125f12f060c5" />


# Result

The Gridworld environment was successfully implemented using a rectangular grid to demonstrate value functions in a finite Markov Decision Process (MDP).  
The state values were computed using iterative policy evaluation and the Bellman equation, showing how the agent estimates the long-term reward for each state in the environment.
