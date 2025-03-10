The same as [[Depth First Search]] but with a ==depth LIMIT==
1. start with fringe = \[initial_state\]
2. pop the first element in the fringe and append its children to the **==START==** of the fringe (if the depth limit hasn't been reached), (popping removes the element from the fringe)
3. Repeat Step 2 until the popped element = goal, or fringe = [] (empty)