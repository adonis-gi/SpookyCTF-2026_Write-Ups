# Demented Memories

- **Category:** Misc
- **Flag:** `spooky{the_g00d_the_l0st_@nd_th3_void}`

## Solution

### 1. Repository Analysis & Part 1
Navigated the local Git repository history to look for wiped or deleted commits:

```bash
git log --all --oneline --source
```

Found commit `0f00424` labeled *MEMORY WIPE INITIALIZATION*. Inspecting its contents (`git show 0f00424`) revealed a deleted script containing Part 1:
`spooky{the_g00d_`

### 2. Part 2 & Part 3 (Hidden Files)
1. Inspected `.git/errored_space.txt`, which contained Part 3 (`th3_void}`) and the clue:
   > *"61, the year the memories cuts through the fog..."*
2. Located the hidden file `.fog61.fog` in the repository directory and extracted the hex payload:
   `7468655f6c3073745f406e6420283229`
3. Decoded the hex string using CyberChef to retrieve Part 2:
   `the_l0st_@nd`

### 3. Flag Reconstruction & Fix
Concatenating all three parts gave `spooky{the_g00d_the_l0st_@ndth3_void}`. 

Since `@ndth3` was missing a separator between words, adding an underscore produced the correct flag:
`spooky{the_g00d_the_l0st_@nd_th3_void}`
