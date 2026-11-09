# Eisoptrophobia

- **Category:** Forensics
- **Flag:** `spooky{the_reflection_never_lies}`

## Solution

1. **Initial Reconnaissance**
   Standard static analysis tools (`strings`, `exiftool`, `binwalk`) didn't reveal any obvious hidden files or suspicious metadata.

2. **Steganography Analysis (`zsteg`)**
   Running `zsteg` across all methods exposed an intriguing LSB payload:
   ```bash
   $ zsteg -a Eisoptrophobiactf.png
   imagedata           .. file: shared library
   chunk:0:IHDR        .. file: Adobe Photoshop Color swatch...
   b1,r,lsb,xy         .. text: "$rGsrYtz"
   b1,g,msb,xy         .. text: "\rlSA~:\t6"
   b1,rgb,lsb,xy       .. text: "c3Bvb2t5e3RoZV9yZWZsZWN0aW9uX25ldmVyX2xpZXN9"
   ```
3. **Decoding & Flag Recovery**
   Filtering through the noise, the string on b1,rgb,lsb,xy (`c3Bvb2t5e3RoZV9yZWZsZWN0aW9uX25ldmVyX2xpZXN9`) was identified as Base64.
   Decoding it in CyberChef produced the final flag: `spooky{the_reflection_never_lies}`
