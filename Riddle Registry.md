# CTF Write-Up: Riddle Registry

* **Platform:** CyLab Security Academy (picoMini by CMU-Africa)
* **Category:** Forensics
* **Difficulty:** Easy
* **Challenge Name:** Riddle Registry

1. Challenge Overview
The challenge presented a PDF file containing what appeared to be garbled nonsense text with covered sections. The goal was to look beyond the visible text and inspect the file's inner properties to uncover a hidden flag.

2. Reconnaissance & Methodology
Initial Inspection: Opened the PDF and noticed text that was covered or obscured. Copying and pasting the text content into Microsoft Word yielded nothing useful.

Hypothesis: Since visible text manipulation failed, the hidden data might not be part of the document body text, but rather stored within the file's properties or metadata.

Tool Selection: ExifTool was selected to inspect the hidden metadata fields of the PDF file.

3. Step-by-Step Solution
Step 1: Extracting Metadata via ExifTool
Ran exiftool on the downloaded PDF document to review embedded fields like Author, Title, Creator, and Description.

Step 2: Locating and Decoding the Base64 String
Upon reviewing the metadata output, a suspicious string ending with = (a telltale sign of Base64 encoding) was discovered inside the author/description field.

The Base64 string was decoded using the Linux terminal command:

echo 'YWNhZGVteXtwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV85ZDNjYzY2OX0=' | base64 -d

4. The Flag
* **academy{puzzl3d_m3tadata_f0und!_9d3cc669}**
5. Key Takeaways
Check the Metadata: Always inspect file metadata (using tools like exiftool) when visual inspection or content extraction of a file yields no results.
File properties frequently harbor hidden clues, notes, or encoded strings left by challenge authors.
