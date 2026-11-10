# Peering Eyes

- **Category:** Forensics
- **Flag:** `spooky{th3y_ar3_w2tch1ng}`

## Solution

### 1. Memory Analysis & Process Identification
Analyzed the Linux memory dump (`spooked2.lime`) using Volatility 3 to list running processes:

```bash
python3 vol -f spooked2.lime -s symbols linux.psaux
```

Identified an intriguing python process:
`28906  2311  python3  python3 EYEsee.py`

### 2. Script Inspection
Searched memory for traces of `EYEsee.py`:

```bash
strings spooked2.lime | grep -i "eyesee"
```

The output revealed error traces pointing to OpenCV (`cv2`) imports and execution, matching the challenge description about taking photos via webcam.

### 3. Carving Images (Part 2)
Extracted embedded JPG images from the memory capture using `foremost`:

```bash
foremost -t jpg -i spooked2.lime -o photos
```

Inspecting the carved images in the output folder revealed a photo of a person holding a piece of paper with Part 2 of the flag written on it:
`w2tch1ng}`

### 4. Memory Search (Part 1)
Searched the raw memory dump directly for the flag prefix to find Part 1:

```bash
strings spooked2.lime | grep "spooky{"
```

Extracted Part 1: `spooky{th3yar3`

### 5. Flag Assembly
Concatenated Part 1 and Part 2, adding the required score underscores for word separation:
`spooky{th3y_ar3_w2tch1ng}`
