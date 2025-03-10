#cryptography 

It is a [[Transposition Cipher]] that shuffles the order of the characters following these steps:
1. Choose a number of rails (rows)
2. Write the plaintext in a zigzag pattern (up and down).
3. Read the rails row by row (left to right).

**Example**
Plaintext: HELLO WORLD
Rails = 3
```mathematica
Rail 1: H . . . O . . . L . . 
Rail 2: . E . L . W . R . D . 
Rail 3: . . L . . . O . . . .
```
Cipher Text: **HOLELWRDLO**