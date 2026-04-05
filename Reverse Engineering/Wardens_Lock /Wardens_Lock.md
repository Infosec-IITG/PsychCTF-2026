Wardens Lock
**Category:** Reverse Engineering

**Objective:** Solve a system of hardcoded mathematical constraints inside a binary to find the correct input.

**Methodology:**
1.  **Decompilation:** Similar to the first challenge, this file (which already had the correct `.out` extension) was decompiled using Dogbolt.org.
2.  **Constraint Extraction:** Analyzing the decompiled C-like pseudocode revealed the validation logic. The program checks the user's input against a series of mathematical conditions involving two variables, $x$ and $y$. The extracted constraints were:
    * `x % 7 == 1`
    * `x + y == 0x125fa` (which is 75258 in decimal)
    * `3y - x == 0xfffeeeea` (which evaluates to the signed integer -69910)
    * `x ^ y == 0x125f8`
3.  **Solving the Equations:** Using the linear equations `x + y = 75258` and `3y - x = -69910`, we can solve for the variables:
    * Adding the two equations together: `(x + y) + (3y - x) = 75258 - 69910`
    * `4y = 5348`  $\rightarrow$  `y = 1337`
    * Substituting `y` back into the first equation: `x + 1337 = 75258` $\rightarrow$ `x = 73921`
4.  **Verification:** Checking against the other constraints: `73921 % 7` equals `1`, and `73921 ^ 1337` correctly yields `0x125f8`. 

> **Flag:** `73921-1337`
