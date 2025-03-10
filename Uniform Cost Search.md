1. Start with fringe = \[(initial_state, 0)\]   ( 0 is the path cast of the intial_state)
2. expand the element with the lowest path cost in the fringe, and add that elements cost the its childrens path cost.
3. sort the fringe based on path cost
4. Repeat Step 2 and 3 until the popped element = goal, or fringe = [] (empty)