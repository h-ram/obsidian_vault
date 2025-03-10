You are given a heuristic table of the heuristic value of each node.
1. start with fringe = \[(initial_state, fn(initial_state)]
2. expand the element with the lowest **f(n)** cost into the fringe (without the parent node)
3. sort the fringe based on **f(n)**.
4. repeat 2 and 3 until reaching goal, or fringe = [] (empty)
---
==**f(n) = gn(n) + h(n)**== , where g(n) is the path cost from initial_node to this node, and h(n) is the heuristic value from the table.