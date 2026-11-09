# I Feel Like Someone's Watching Me

- **Category:** Crypto
- **Flag:** `spooky{eyez_are_watching_me}`

## Solution

1. **Cipher Identification**
   Recognized that the ciphertext was encrypted using a monoalphabetic substitution cipher.

2. **Frequency Analysis**
   Used [quipqiup](https://quipqiup.com/) to perform automated frequency analysis and break the substitution cipher.

3. **Clue Extraction & Flag Formatting**
   The decoded text contained the following trailing message:
   > *"But I'll put a clue that should help you find me if you still care. eyez are watching me. Just remember underscores instead of spaces and to wrap it correctly. I hope you find me before they do. Sincerely, The One You Left Behind"*

   Following the instructions:
   - Extracted the clue: `eyez are watching me`
   - Replaced spaces with underscores: `eyez_are_watching_me`
   - Wrapped it in the CTF flag format: `spooky{eyez_are_watching_me}`
