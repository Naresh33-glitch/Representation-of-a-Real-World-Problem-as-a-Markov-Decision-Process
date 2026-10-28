# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process


## Aim

To represent a real-world smart vacuum cleaning robot problem as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, reward function, and implementing the model using Python dictionaries.


Example:


A smart vacuum robot starts from its charging station, moves to a dirty area, cleans it, avoids obstacles if encountered, and finally returns after completing the cleaning task. The robot learns to choose actions that maximize the total reward while minimizing unnecessary movements and collisions.

---

## Problem Statement

### Problem Description

A smart vacuum cleaning robot cleans a small room. It starts from the charging station, moves around to clean dirty areas, avoids obstacles, and returns to the charging station after finishing. The robot receives positive rewards for cleaning and returning safely, while hitting an obstacle results in a negative reward. This can be modeled as a Markov Decision Process (MDP).


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

Write your answer here.

The state space should list all possible situations in which the agent can exist.

Example format:

```text
S = {
    Charging Station,
    Dirty Area,
    Clean Area,
    Obstacle,
    Task Complete
}
```



---

## Sample State



A sample state is one specific example from the state space.
```
Dirty Area
```
---

## Action Space



The action space should list all possible actions available to the agent.

Example format:

```text
A = {
    Move,
    Clean,
    Avoid,
    Return
}
```


---

## Sample Action


A sample action is one action selected from the action space.
```
Clean
```


---

## Transition Probability

```
P(s' | s, a)

Charging Station --Move--> Dirty Area (1.0)

Dirty Area --Clean--> Clean Area (0.9)

Dirty Area --Move--> Obstacle (0.1)

Obstacle --Avoid--> Dirty Area (1.0)

Clean Area --Return--> Task Complete (1.0)
```

The transition probability explains how the environment moves from one state to another after an action is taken.

General form:

$$
P(s' \mid s,a)
$$

This means:

> Probability of reaching next state $s'$ after taking action $a$ in current state $s$.


---

## Reward Function


The reward function defines the feedback received by the agent after taking an action.
```
R(s, a, s')

Charging Station → Dirty Area = -1

Dirty Area → Clean Area = +10

Dirty Area → Obstacle = -10

Obstacle → Dirty Area = -2

Clean Area → Task Complete = +20
```
General form:

```
R(s,a,s′)
```

---

## Graphical Representation





The graph should include:

1. States as nodes.
2. Actions as arrows.
3. Rewards on transitions.
4. Transition probabilities if applicable.

<img width="1508" height="704" alt="MDP" src="https://github.com/user-attachments/assets/1c2e10a6-1f5a-4066-977d-144e0efbb00b" />

---

## Python Representation

```python
# MDP Representation using Python
# States
# MDP Representation as a Dictionary

mdp = {
    "states": {
        0: "Charging Station",
        1: "Dirty Area",
        2: "Clean Area",
        3: "Obstacle",
        4: "Task Complete"
    },

    "actions": {
        0: "Move",
        1: "Clean",
        2: "Avoid",
        3: "Return"
    },

    "transitions": {
        ("Charging Station", "Move"): {
            "next_state": "Dirty Area",
            "probability": 1.0
        },
        ("Dirty Area", "Clean"): {
            "next_state": "Clean Area",
            "probability": 0.9
        },
        ("Dirty Area", "Move"): {
            "next_state": "Obstacle",
            "probability": 0.1
        },
        ("Obstacle", "Avoid"): {
            "next_state": "Dirty Area",
            "probability": 1.0
        },
        ("Clean Area", "Return"): {
            "next_state": "Task Complete",
            "probability": 1.0
        }
    },

    "rewards": {
        ("Charging Station", "Move", "Dirty Area"): -1,
        ("Dirty Area", "Clean", "Clean Area"): 10,
        ("Dirty Area", "Move", "Obstacle"): -10,
        ("Obstacle", "Avoid", "Dirty Area"): -2,
        ("Clean Area", "Return", "Task Complete"): 20
    },

    "discount_factor": 0.9
}

# Display the MDP
for key, value in mdp.items():
    print(f"\n{key.upper()}:")
    print(value)
print("Name : S.Naresh      ")
print("Register Number:212224240101  ")
```
---
## Output

<img width="1024" height="337" alt="image" src="https://github.com/user-attachments/assets/4fbd68b5-e71f-4820-be00-83d443413a0e" />



---

## Result


The smart vacuum cleaning robot problem was successfully represented as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, reward function, and discount factor. The MDP was implemented using Python dictionaries, enabling the robot to make optimal sequential decisions for efficient cleaning while avoiding obstacles and completing the task successfully.


---

