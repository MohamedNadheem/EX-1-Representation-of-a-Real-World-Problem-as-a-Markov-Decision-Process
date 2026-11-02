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

<img width="1408" height="768" alt="Gemini_Generated_Image_o0nmrlo0nmrlo0nm" src="https://github.com/user-attachments/assets/5c13829f-1809-4bcb-9920-0f79d03cffb3" />



---

## Python Representation
```
# MDP Representation using Python

print("Name: [Your Name]")
print("Register Number: [Your Register Number]")

states = ["Shelf Empty", "Item Loaded", "Path Blocked"]

actions = [
    "Move Forward",
    "Turn Left",
    "Turn Right",
    "Pick Item"
]

transition_probability = {
    ("Shelf Empty", "Pick Item"): {
        "Item Loaded": 0.85,
        "Shelf Empty": 0.15
    },
    ("Item Loaded", "Move Forward"): {
        "Shelf Empty": 0.5,
        "Item Loaded": 0.5
    },
    ("Shelf Empty", "Move Forward"): {
        "Path Blocked": 0.25,
        "Shelf Empty": 0.75
    },
    ("Path Blocked", "Turn Right"): {
        "Shelf Empty": 0.6,
        "Path Blocked": 0.4
    }
}

rewards = {
    ("Shelf Empty", "Pick Item", "Item Loaded"): 15,
    ("Item Loaded", "Move Forward", "Shelf Empty"): 3,
    ("Shelf Empty", "Move Forward", "Path Blocked"): -12,
    ("Path Blocked", "Turn Right", "Shelf Empty"): 4
}

discount_factor = 0.95

print("States:", states)
print("Actions:", actions)
print("Transition Probability:", transition_probability)
print("Rewards:", rewards)
print("Discount Factor:", discount_factor)
```
---
## Output
```
Name: Mohamed Nadheem N
Register Number: 212223240091
States: ['Shelf Empty', 'Item Loaded', 'Path Blocked']
Actions: ['Move Forward', 'Turn Left', 'Turn Right', 'Pick Item']
Transition Probability: {('Shelf Empty', 'Pick Item'): {'Item Loaded': 0.85, 'Shelf Empty': 0.15}, ('Item Loaded', 'Move Forward'): {'Shelf Empty': 0.5, 'Item Loaded': 0.5}, ('Shelf Empty', 'Move Forward'): {'Path Blocked': 0.25, 'Shelf Empty': 0.75}, ('Path Blocked', 'Turn Right'): {'Shelf Empty': 0.6, 'Path Blocked': 0.4}}
Rewards: {('Shelf Empty', 'Pick Item', 'Item Loaded'): 15, ('Item Loaded', 'Move Forward', 'Shelf Empty'): 3, ('Shelf Empty', 'Move Forward', 'Path Blocked'): -12, ('Path Blocked', 'Turn Right', 'Shelf Empty'): 4}
Discount Factor: 0.95
```

---

## Result

The Autonomous Warehouse Inventory Robot was successfully represented as a Markov Decision Process (MDP) by defining its state space, action space, transition probabilities, reward function, graphical representation, and Python implementation. This model demonstrates how reinforcement learning can be applied to enable a warehouse robot to retrieve items efficiently, avoid blocked paths, optimize routing, and maximize long-term operational performance.

---
