The same as [[Depth Limited Search]] but with a But the ==LIMIT starts from 0 to last level==, or until goal is reached.

1. Start at limit=0
	1. start with fringe = \[initial_state\]
	2. pop the first element in the fringe and append its children to the **==START==** of the fringe (if the depth limit hasn't been reached), (popping removes the element from the fringe)
	3. Repeat Step 2 until the popped element = goal, or fringe = [] (empty)
2. Increment limit (limit+1) and repeat until max depth