# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process


## Aim
To represent an Autonomous Warehouse Inventory Robot as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, reward function, and Python representation.

---

## Problem Statement
Design a decision-making model for an intelligent warehouse inventory robot that learns to navigate storage aisles efficiently by selecting appropriate retrieval and movement actions while maximizing total operational rewards.

### Problem Description

An inventory robot operates autonomously inside a fulfillment center. At every step, it decides the best action—such as moving forward, turning left, turning right, or picking an item—based on its current shelf and aisle conditions. Depending on the chosen action, it may successfully retrieve an item, encounter a blocked path, or reach an empty shelf. The robot receives positive rewards for successful item retrieval and efficient navigation, and negative rewards for collisions, incorrect handling, or blocked paths. This problem is represented as a Markov Decision Process (MDP), where the robot learns the optimal sequence of actions to maximize long-term operational efficiency.


---

## MDP Components

A Markov Decision Process is represented as: 

$$
MDP = (S, A, P, R, \gamma)
$$

Where:

| Symbol | Meaning |
|---|---|
| $S$ | Set of states |
| $A$ | Set of actions |
| $P$ | Transition probability function |
| $R$ | Reward function |
| $\gamma$ | Discount factor |

---

## State Space

The state space represents all possible conditions of the warehouse robot.

```
S = {
    Shelf Empty,
    Item Loaded,
    Path Blocked
}
```



---

## Sample State

Item Loaded

The robot is currently carrying a retrieved inventory item and navigating toward the packing station.


---

## Action Space
The action space represents all possible actions the robot warehouse can perform.

```
A = {
    Move Forward,
    Turn Left,
    Turn Right,
    Pick Item
}
```

---

## Sample Action

Pick Item

The robot engages its mechanical arm to lift and secure an item from the storage shelf.


---

## Transition Probability

The transition probability explains how the environment moves from one state to another after an action is taken.

General form:

$$
P(s' \s,a)
$$

This means:

> Probability of reaching next state $s'$ after taking action $a$ in current state $s$.


Example:

P(Item Loaded | Shelf Empty, Pick Item) = 0.85

P(Shelf Empty | Item Loaded, Move Forward) = 0.50

P(Path Blocked | Shelf Empty, Move Forward) = 0.25

P(Path Blocked | Path Blocked, Turn Right) = 0.40

---

## Reward Function

The reward function provides feedback to the warehouse robot after performing an action.

General form:

$$
R(s,a,s')
$$

Example Rewards:

Successfully retrieved an item = +15

Moved efficiently = +3

Hit an obstacle = -12

Unnecessary movement = -2

---

## Graphical Representation

<img width="1033" height="766" alt="Screenshot 2026-07-29 211634" src="https://github.com/user-attachments/assets/f9107d80-cc74-4651-911d-9989b0b0423b" />


---

## Python Representation
```
# MDP Representation using Python

print("Name: shruthi D N")
print("Register Number: 212223240155")

states = ["Clean Area", "Dirty Area", "Obstacle Detected"]

actions = [
    "Move Forward",
    "Turn Left",
    "Turn Right",
    "Clean Area"
]

transition_probability = {
    ("Dirty Area", "Clean Area"): {
        "Clean Area": 0.9,
        "Dirty Area": 0.1
    },
    ("Clean Area", "Move Forward"): {
        "Dirty Area": 0.6,
        "Clean Area": 0.4
    },
    ("Dirty Area", "Move Forward"): {
        "Obstacle Detected": 0.2,
        "Dirty Area": 0.8
    },
    ("Obstacle Detected", "Turn Right"): {
        "Dirty Area": 0.7,
        "Obstacle Detected": 0.3
    }
}

rewards = {
    ("Dirty Area", "Clean Area", "Clean Area"): 10,
    ("Clean Area", "Move Forward", "Dirty Area"): 2,
    ("Dirty Area", "Move Forward", "Obstacle Detected"): -10,
    ("Obstacle Detected", "Turn Right", "Dirty Area"): 5
}

discount_factor = 0.9

print("States:", states)
print("Actions:", actions)
print("Transition Probability:", transition_probability)
print("Rewards:", rewards)
print("Discount Factor:", discount_factor)
```
---
## Output
```
Name: shruthi D N
Register Number: 212223240155
States: ['Clean Area', 'Dirty Area', 'Obstacle Detected']
Actions: ['Move Forward', 'Turn Left', 'Turn Right', 'Clean Area']
Transition Probability: {('Dirty Area', 'Clean Area'): {'Clean Area': 0.9, 'Dirty Area': 0.1}, ('Clean Area', 'Move Forward'): {'Dirty Area': 0.6, 'Clean Area': 0.4}, ('Dirty Area', 'Move Forward'): {'Obstacle Detected': 0.2, 'Dirty Area': 0.8}, ('Obstacle Detected', 'Turn Right'): {'Dirty Area': 0.7, 'Obstacle Detected': 0.3}}
Rewards: {('Dirty Area', 'Clean Area', 'Clean Area'): 10, ('Clean Area', 'Move Forward', 'Dirty Area'): 2, ('Dirty Area', 'Move Forward', 'Obstacle Detected'): -10, ('Obstacle Detected', 'Turn Right', 'Dirty Area'): 5}
Discount Factor: 0.9
```

---

## Result

The Robot Vacuum Cleaner was successfully represented as a Markov Decision Process (MDP) by defining its state space, action space, transition probabilities, reward function, graphical representation, and Python implementation. This model demonstrates how reinforcement learning can be applied to enable a robot vacuum cleaner to clean efficiently, avoid obstacles, conserve battery power, and maximize long-term cleaning performance.

---
