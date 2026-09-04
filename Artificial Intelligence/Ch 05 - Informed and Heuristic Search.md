# Chapter 5: Informed and Heuristic Search

## Introduction to Informed Search

Informed search algorithms use problem-specific knowledge to guide the search towards promising solutions. Key characteristics of informed search include:

- **Heuristic information**: The search is guided by problem-specific knowledge
- **Efficiency**: Informed search is more efficient than uninformed search
- **Optimality**: Informed search can find optimal solutions more efficiently

## Heuristics

Heuristics are problem-specific rules or strategies that guide the search towards promising solutions. Key properties of heuristics include:

- **Admissibility**: A heuristic is admissible if it never overestimates the cost to reach the goal
- **Consistency**: A heuristic is consistent if it satisfies the triangle inequality
- **Informativeness**: A heuristic is informative if it provides useful information to guide the search

## Greedy Best-First Search

### Intuition

Greedy best-first search explores the most promising nodes first based on a heuristic function. It is not optimal for finding the shortest path but is efficient in terms of time and space.

### Problem Solved

Greedy best-first search finds a solution path but not necessarily the shortest path.

### Step-by-Step Working

1. Start at the initial state
2. Evaluate the heuristic value of each neighboring state
3. Choose the state with the lowest heuristic value and explore it
4. Repeat the process until the goal is found

### Pseudocode

```python
import heapq

def greedy_best_first_search(initial_state, goal_test, successors, heuristic):
    frontier = [(heuristic(initial_state), initial_state)]
    explored = set()
    
    while frontier:
        _, state = heapq.heappop(frontier)
        if goal_test(state):
            return state
        explored.add(state)
        for child in successors(state):
            if child not in explored and child not in [s for _, s in frontier]:
                heapq.heappush(frontier, (heuristic(child), child))
    return None
```

### Example

Consider a simple maze problem where the agent needs to find the shortest path from the start to the goal. Greedy best-first search will explore the most promising paths based on the heuristic function.

### Time Complexity

- **O(b^m)**: Where b is the branching factor and m is the maximum depth of the state space

### Space Complexity

- **O(bm)**: The space required to store the frontier and explored set

### Completeness

Greedy best-first search is not complete for infinite state spaces.

### Optimality

Greedy best-first search is not optimal for finding the shortest path.

### Advantages

- More efficient than uninformed search in terms of time and space
- Simple to implement

### Limitations

- Not optimal for finding the shortest path
- Can get stuck in local optima

## A* Search

### Intuition

A* search combines the benefits of uniform cost search and greedy best-first search. It uses both the cost to reach the current state and the heuristic estimate to the goal to guide the search.

### Problem Solved

A* search finds the shortest path in a weighted state space.

### Step-by-Step Working

1. Start at the initial state with a cost of 0
2. Evaluate the heuristic value of each neighboring state
3. Choose the state with the lowest f(n) = g(n) + h(n) and explore it
4. Update the cost of each state and repeat the process until the goal is found

### Pseudocode

```python
import heapq

def a_star_search(initial_state, goal_test, successors, heuristic, cost):
    frontier = [(heuristic(initial_state), 0, initial_state)]
    explored = set()
    
    while frontier:
        _, total_cost, state = heapq.heappop(frontier)
        if goal_test(state):
            return state
        explored.add(state)
        for child, step_cost in successors(state):
            if child not in explored:
                new_cost = total_cost + step_cost
                heapq.heappush(frontier, (new_cost + heuristic(child), new_cost, child))
    return None
```

### Example

Consider a weighted graph where each edge has a cost. A* search will find the shortest path from the start to the goal by combining the cost to reach the current state and the heuristic estimate to the goal.

### Time Complexity

- **O(b^(C*/ε))**: Where C* is the cost of the optimal solution and ε is the smallest cost of any action

### Space Complexity

- **O(b^(C*/ε))**: The space required to store the frontier and explored set

### Completeness

A* search is complete for finite state spaces.

### Optimality

A* search is optimal for weighted state spaces.

### Advantages

- Guaranteed to find the shortest path in a weighted state space
- More efficient than uninformed search in terms of time and space

### Limitations

- Not suitable for large state spaces due to high time and space complexity
- Requires knowledge of the cost of each action and a heuristic function

## Heuristic Design

### Heuristic Functions

Heuristic functions estimate the cost from the current state to the goal. Key types of heuristic functions include:

- **Admissible heuristics**: Never overestimate the cost to reach the goal
- **Consistent heuristics**: Satisfy the triangle inequality
- **Dominance heuristics**: Provide a lower bound on the actual cost

### Heuristic Evaluation

Heuristic evaluation involves assessing the quality of a heuristic function. Key criteria for evaluating heuristics include:

- **Admissibility**: Does the heuristic never overestimate the cost to reach the goal?
- **Consistency**: Does the heuristic satisfy the triangle inequality?
- **Informativeness**: Does the heuristic provide useful information to guide the search?

## Applications of Informed Search

- **Robotics**: Path planning and navigation
- **Game playing**: Finding the best move in a game
- **Planning**: Generating a sequence of actions to achieve a goal
- **Scheduling**: Allocating resources to tasks over time
- **Logistics**: Optimizing the distribution of goods

## Challenges in Informed Search

- **Heuristic design**: Designing effective heuristics for complex problems
- **Search efficiency**: Balancing the need for completeness and optimality with the need for efficiency
- **Heuristic evaluation**: Assessing the quality of heuristic functions

## Future Directions in Informed Search

- **Machine learning**: Using machine learning to improve heuristic functions
- **Hybrid approaches**: Combining informed search with other AI techniques such as constraint satisfaction and optimization
- **Explainable AI**: Making search decisions more understandable

## Conclusion

Informed search algorithms are essential for solving complex problems in AI. By studying greedy best-first search and A* search, we can create AI systems that use problem-specific knowledge to guide the search towards promising solutions and find optimal solutions more efficiently.