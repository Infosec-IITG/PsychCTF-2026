Broken Terminal
**Category:** Reverse Engineering

**Objective:** Extract the hidden flag from a provided binary file.

**Methodology:**
1.  **Initial Inspection:** The provided challenge file was missing a file extension. Standard practice dictated treating it as an executable/binary, effectively acting as an `.out` file.
2.  **Decompilation:** To understand the program's underlying logic without executing it dynamically, I uploaded the binary to [Dogbolt.org](https://dogbolt.org/) (a web-based decompiler explorer).
3.  **Static Analysis:** Using the Hex-Rays decompiler output provided by Dogbolt, I analyzed the source code structure. 
4.  **Flag Extraction:** I located a specific function named `win()`, which is a common convention in CTF challenges for the function that prints the flag. Reviewing the pseudocode inside `win()` revealed the flag in plain text.

> **Flag:** `psych{0v3rfl0w_0p3n3d_th3_c3ll}
