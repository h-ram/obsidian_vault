You are given a heuristic table of the heuristic value of each node.
1. start with fringe = \[(initial_state, fn(initial_state))]
2. expand the element with the lowest **f(n)** cost into the fringe (without parrent node)
3. sort the fringe based on **f(n)**.
4. repeat 2 and 3 until reaching goal, or fringe = [] (empty)
---
 ==**f(n) = h(n)**== , where h(n) is the heuristic value from the table.