# Chapter 4: Uninformed Search Algorithms

## Introduction to Uninformed Search

Uninformed search algorithms are search strategies that do not use any problem-specific knowledge. They explore the state space systematically, without any guidance towards the goal. Key characteristics of uninformed search include:

- **No heuristic information**: The search is not guided by any problem-specific knowledge
- **Systematic exploration**: The state space is explored in a systematic manner
- **Guaranteed to find a solution**: If a solution exists, uninformed search will eventually find it

## Breadth-First Search (BFS)

### Intuition

Breadth-first search explores all nodes at the present depth level before moving on to nodes at the next depth level. It is complete and optimal for unweighted state spaces.

### Problem Solved

BFS finds the shortest path in an unweighted state space.

### Step-by-Step Working

1. Start at the initial state
2. Explore all neighboring states at the current depth level
3. Move to the next depth level and repeat the process

### Pseudocode

```python
from collections import deque

def bfs(initial_state, goal_test, successors):
    frontier = deque([initial_state])
    explored = set()
    
    while frontier:
        state = frontier.popleft()
        if goal_test(state):
            return state
        explored.add(state)
        for child in successors(state):
            if child not in explored and child not in frontier:
                frontier.append(child)
    return None
```

### Example

Consider a simple maze problem where the agent needs to find the shortest path from the start to the goal. BFS will explore all possible paths level by level until it finds the shortest path to the goal.

### Time Complexity

- **O(b^d)**: Where b is the branching factor and d is the depth of the shallowest solution

### Space Complexity

- **O(b^d)**: The space required to store the frontier and explored set

### Completeness

BFS is complete for finite state spaces.

### Optimality

BFS is optimal for unweighted state spaces.

### Advantages

- Guaranteed to find the shortest path in an unweighted state space
- Simple to implement

### Limitations

- Not suitable for large state spaces due to high time and space complexity
- Not optimal for weighted state spaces

## Depth-First Search (DFS)

### Intuition

Depth-first search explores as far as possible along each branch before backtracking. It is not optimal for finding the shortest path but is memory efficient.

### Problem Solved

DFS finds a solution path but not necessarily the shortest path.

### Step-by-Step Working

1. Start at the initial state
2. Choose a child node and explore it deeply
3. Backtrack when a dead end is reached
4. Repeat the process until the goal is found

### Pseudocode

```python
def dfs(initial_state, goal_test, successors):
    frontier = [initial_state]
    explored = set()
    
    while frontier:
        state = frontier.pop()
        if goal_test(state):
            return state
        explored.add(state)
        for child in successors(state):
            if child not in explored and child not in frontier:
                frontier.append(child)
    return None
```

### Example

Consider a simple puzzle problem where the agent needs to find a solution path. DFS will explore one path deeply before backtracking and trying another path.

### Time Complexity

- **O(b^m)**: Where b is the branching factor and m is the maximum depth of the state space

### Space Complexity

- **O(bm)**: The space required to store the frontier and explored set

### Completeness

DFS is complete for finite state spaces.

### Optimality

DFS is not optimal for finding the shortest path.

### Advantages

- Memory efficient for large state spaces
- Simple to implement

### Limitations

- Not optimal for finding the shortest path
- Can get stuck in infinite loops for infinite state spaces

## Uniform Cost Search

### Intuition

Uniform cost search explores the least-cost nodes first. It is optimal for weighted state spaces where the cost of each action is known.

### Problem Solved

Uniform cost search finds the least-cost path in a weighted state space.

### Step-by-Step Working

1. Start at the initial state with a cost of 0
2. Explore the least-cost neighboring states
3. Update the cost of each state and repeat the process

### Pseudocode

```python
import heapq

def uniform_cost_search(initial_state, goal_test, successors, cost):
    frontier = [(0, initial_state)]
    explored = set()
    
    while frontier:
        total_cost, state = heapq.heappop(frontier)
        if goal_test(state):
            return state
        explored.add(state)
        for child, step_cost in successors(state):
            if child not in explored:
                heapq.heappush(frontier, (total_cost + step_cost, child))
    return None
```

### Example

Consider a weighted graph where each edge has a cost. Uniform cost search will find the least-cost path from the start to the goal.

### Time Complexity

- **O(b^(C*/ε))**: Where C* is the cost of the optimal solution and ε is the smallest cost of any action

### Space Complexity

- **O(b^(C*/ε))**: The space required to store the frontier and explored set

### Completeness

Uniform cost search is complete for finite state spaces.

### Optimality

Uniform cost search is optimal for weighted state spaces.

### Advantages

- Guaranteed to find the least-cost path in a weighted state space
- Simple to implement

### Limitations

- Not suitable for large state spaces due to high time and space complexity
- Requires knowledge of the cost of each action

## Depth-Limited Search

### Intuition

Depth-limited search is a variant of DFS that limits the depth of the search. It is used to prevent infinite loops in infinite state spaces.

### Problem Solved

Depth-limited search finds a solution path within a specified depth limit.

### Step-by-Step Working

1. Start at the initial state
2. Explore nodes up to the specified depth limit
3. Backtrack when the depth limit is reached
4. Repeat the process until the goal is found

### Pseudocode

```python
def depth_limited_search(initial_state, goal_test, successors, limit):
    frontier = [(initial_state, 0)]
    explored = set()
    
    while frontier:
        state, depth = frontier.pop()
        if goal_test(state):
            return state
        if depth < limit:
            explored.add(state)
            for child in successors(state):
                if child not in explored and child not in [s for s, d in frontier]:
                    frontier.append((child, depth + 1))
    return None
```

### Example

Consider a simple puzzle problem where the agent needs to find a solution path within a specified depth limit. Depth-limited search will explore nodes up to the specified depth limit.

### Time Complexity

- **O(b^l)**: Where b is the branching factor and l is the depth limit

### Space Complexity

- **O(bl)**: The space required to store the frontier and explored set

### Completeness

Depth-limited search is not complete for infinite state spaces.

### Optimality

Depth-limited search is not optimal for finding the shortest path.

### Advantages

- Prevents infinite loops in infinite state spaces
- Memory efficient for large state spaces

### Limitations

- Not complete for infinite state spaces
- Not optimal for finding the shortest path

## Iterative Deepening Search

### Intuition

Iterative deepening search combines the benefits of BFS and DFS. It performs a series of depth-limited searches with increasing depth limits until the goal is found.

### Problem Solved

Iterative deepening search finds the shortest path in an unweighted state space.

### Step-by-Step Working

1. Start with a depth limit of 0
2. Perform a depth-limited search with the current depth limit
3. Increase the depth limit and repeat the process until the goal is found

### Pseudocode

```python
def iterative_deepening_search(initial_state, goal_test, successors):
    depth = 0
    while True:
        result = depth_limited_search(initial_state, goal_test, successors, depth)
        if result is not None:
            return result
        depth += 1
```

### Example

Consider a simple maze problem where the agent needs to find the shortest path from the start to the goal. Iterative deepening search will perform a series of depth-limited searches with increasing depth limits until the shortest path to the goal is found.

### Time Complexity

- **O(b^d)**: Where b is the branching factor and d is the depth of the shallowest solution

### Space Complexity

- **O(bd)**: The space required to store the frontier and explored set

### Completeness

Iterative deepening search is complete for finite state spaces.

### Optimality

Iterative deepening search is optimal for unweighted state spaces.

### Advantages

- Guaranteed to find the shortest path in an unweighted state space
- Memory efficient for large state spaces

### Limitations

- Not suitable for large state spaces due to high time complexity
- Not optimal for weighted state spaces

## Bidirectional Search

### Intuition

Bidirectional search involves performing two simultaneous searches: one forward from the initial state and one backward from the goal state. The two searches meet in the middle.

### Problem Solved

Bidirectional search finds the shortest path in an unweighted state space.

### Step-by-Step Working

1. Start a forward search from the initial state
2. Start a backward search from the goal state
3. Continue the searches until they meet in the middle
4. Combine the paths from the forward and backward searches to find the shortest path

### Pseudocode

```python
def bidirectional_search(initial_state, goal_state, goal_test, forward_successors, backward_successors):
    forward_frontier = [initial_state]
    backward_frontier = [goal_state]
    forward_explored = set()
    backward_explored = set()
    
    while forward_frontier and backward_frontier:
        forward_state = forward_frontier.pop()
        backward_state = backward_frontier.pop()
        
        if forward_state in backward_explored or backward_state in forward_explored:
            return forward_state, backward_state
        
        forward_explored.add(forward_state)
        backward_explored.add(backward_state)
        
        for child in forward_successors(forward_state):
            if child not in forward_explored and child not in forward_frontier:
                forward_frontier.append(child)
        
        for child in backward_successors(backward_state):
            if child not in backward_explored and child not in backward_frontier:
                backward_frontier.append(child)
    
    return None
```

### Example

Consider a simple maze problem where the agent needs to find the shortest path from the start to the goal. Bidirectional search will perform two simultaneous searches until they meet in the middle.

### Time Complexity

- **O(b^(d/2))**: Where b is the branching factor and d is the depth of the shallowest solution

### Space Complexity

- **O(b^(d/2))**: The space required to store the frontier and explored set

### Completeness

Bidirectional search is complete for finite state spaces.

### Optimality

Bidirectional search is optimal for unweighted state spaces.

### Advantages

- More efficient than unidirectional search for large state spaces
- Guaranteed to find the shortest path in an unweighted state space

### Limitations

- Not suitable for large state spaces due to high time and space complexity
- Not optimal for weighted state spaces

## Conclusion

Uninformed search algorithms are essential for solving problems in AI. By studying BFS, DFS, uniform cost search, depth-limited search, iterative deepening search, and bidirectional search, we can create AI systems that can explore the state space systematically and find solutions to complex problems.