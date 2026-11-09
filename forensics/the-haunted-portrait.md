# The Haunted Portrait

- **Category:** Forensics

## Solution

### 1. Color Channel Manipulation
Similar to *Stash The Hash*, the hidden payload was embedded within the image's color planes.

### 2. Steganography Analysis
Uploaded the image to [StegOnline](https://georgeom.net/StegOnline/) and inspected the bit planes to reveal the hidden string.

### 3. Flag Extraction
Decoded the extracted payload using CyberChef to retrieve the final flag.
