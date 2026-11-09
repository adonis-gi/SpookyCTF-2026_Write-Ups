# Stash The Hash

- **Category:** Forensics
- **Flag:** `spooky{dleeds_isa_devil}`

## Solution

1. **Archive Extraction**
   The password provided in the `.txt` file was an MD5 hash. Decoding the hash yielded the archive password: `newjerseydevils`.
   Using this password, I extracted the `.7z` archive to get a `.png` image.

2. **Steganography Analysis**
   - Loaded the extracted `.png` into [StegOnline](https://georgeom.net/StegOnline/).
   - Used the **Browse Bit Plane** option to inspect the individual color channels and layers.

3. **Flag Recovery**
   The flag was visually concealed within the bit planes and read directly:
   `spooky{dleeds_isa_devil}`
