# Challenge 3: Hidden in Plain Sight

**Category:** Digital Forensics / Steganography (Medium, 300 points)
**Goal:** Find data hidden in an image described as "just abstract art".
**Hint:** "Standard metadata tools won't find anything. Think smaller, pixel-level small."
**Flag:** `DYPU{REDACTED}`

## Approach

1. **Read the hint as a pointer to pixel-level steganography.** "Pixel-level small" suggests the least significant bits (LSBs) of the colour values.

2. **Extracted the archive.** It contained `challenge.png` and a `README.txt`. The README only restated the hint, so the data had to be inside the image.

3. **Ruled out metadata.** `exiftool -a -G1` showed only standard PNG properties, with no comments or text chunks. It did show something important: the file is an **8-bit RGB, lossless (Deflate) PNG**. Lossless compression preserves every colour value exactly, including the LSBs, which makes it ideal for LSB steganography. A lossy JPEG would destroy them.

4. **Confirmed nothing was readable in the raw bytes.** Loading the file into CyberChef with no recipe showed only normal PNG structure (`‰PNG`, `IHDR`, `IDAT`).

5. **Extracted the LSBs.** In CyberChef, I used **Extract LSB** with Colour Pattern `R, G, B`, Pixel Order `Row`, and Bit `0`. This takes the lowest bit of each red, green and blue value, pixel by pixel, and joins them into bytes. The flag appeared at the start of the output.

6. **Sanity-checked the output size.** The output was 93,750 bytes = 500 × 500 pixels × 3 channels ÷ 8, which confirms every LSB was read. Everything after the flag is noise from untouched pixels. Submitted and accepted.

## Why it's "hidden in plain sight"

Changing only the last bit of a colour value shifts it by at most 1/255, which is invisible to the eye. That's why the image looks completely normal.

## Lessons

- The file format matters. Lossless formats (PNG, BMP) can carry LSB payloads; lossy formats (JPEG) can't.
- Checking the output size against the image dimensions is a quick way to confirm an extraction covered every pixel.
