# CTF Write-Up: Hidden in plain sight

* **Platform:** CyLab Security Academy (picoMini by CMU-Africa)
* **Category:** Forensics
* **Difficulty:** Easy
* **Challenge Name:** Hidden in plain sight

  1. Challenge Overview
The challenge provided a seemingly ordinary JPG image file. However,
 a payload was steganographically hidden out of sight inside the file, requiring multi-step reconnaissance and extraction to recover the flag.

2. Reconnaissance & Methodology
Initial Inspection: Since visual inspection of the image showed nothing unusual,
the first logical step for image forensics is examining file metadata and embedded comments.

Tool Selection: ExifTool was used to inspect the file properties, 
followed by Base64 decoding for any encoded strings, and Steghide to extract the hidden file payload.

3. Step-by-Step Solution
Step 1: Extracting Metadata with ExifTool
Ran exiftool on the target image file to check embedded tags. This revealed a custom string of text located in the Comment field.

Step 2: Multi-Layer Base64 Decoding
The text found in the comment was encoded in Base64.

Performing a first round of Base64 decoding yielded another encoded string ending with =.

Decoding that resulting line a second time successfully revealed the hidden password string:
**pAzzword**

Step 3: Steganography Extraction via Steghide
With the password discovered, the hidden payload embedded inside the image was extracted using steghide:

**steghide extract -sf img.jpg**

4. The Flag
**academy{h1dd3n_1n_1m4g3_d0c4a4e2}**

5. Key Takeaways
Nested Encoding: Challenge authors often hide clues behind multiple layers of standard encodings (like double Base64) inside file metadata.

Steganography Tools: steghide is a staple forensics utility for hiding and extracting data within image and audio files, often requiring a passphrase discovered through preliminary file analysis.
