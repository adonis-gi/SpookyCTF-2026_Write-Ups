# Phasmophobia

- **Category:** Forensics
- **Flag:** `spooky{OOOGABOOGABOOGABOOspoopedBOOgotyou}`

## Solution

### 1. Challenge Overview
The flag was split into two parts: the first embedded in an audio file (`.wav`) and the second hidden inside an image file (`.png`).

### 2. Part 1: Audio Analysis (.wav)
Analyzing the `.wav` file in a spectrogram viewer revealed encoded text drawn visually in the upper frequency spectrum:
`WWWOIJWWOIJWWOIJWWaxwwxml`

### 3. Part 2: Image Analysis (.png)
Running `zsteg` on `ebersecret.png` extracted a hidden LSB text string:

```bash
$ zsteg ebersecret.png
imagedata           .. file: amd 29k coff noprebar executable
b1,rgb,lsb,xy       .. text: "JWWowbgwc (2) (18 salads. yummers)"
```
The clue `18 salads` pointed to a Caesar Cipher shift of 18 (ROT-18), referencing Caesar salad.

### 4. Decryption & Flag Assembly
- Decrypting Part 2: Applying ROT-18 to `JWWowbgwc` produced `BOOgotyou`.
- Decrypting Part 1: Applying ROT-18 to `WWWOIJWWOIJWWOIJWWaxwwxml` produced `OOOGABOOGABOOGABOOspooped.`
- Reconstruction: Concatenating Part 1 + Part 2 and wrapping in the flag format yielded the final flag: `spooky{OOOGABOOGABOOGABOOspoopedBOOgotyou}`
