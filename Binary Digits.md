# CTF Write-Up: Binary Digits

* **Platform:** CyLab Security Academy (picoCTF 2026)
Category: Forensics
Difficulty: Easy
Challenge Name: Binary Digits


1. Challenge Overview
The challenge provided a file that initially "doesn't look like much... just a bunch of 1s and 0s". The core objective was to determine if the text file contained hidden data or structural meaning rather than random noise, and to recover the hidden information.

2. Reconnaissance & Methodology
Initial Inspection: Opening the provided file revealed a continuous sequence of binary digits (0 and 1).

Hypothesis: Since raw binary data can sometimes represent pixel maps or raw image bytes, transforming the text-based binary string into a visual format was the logical next step.

Tool Selection: CyberChef was chosen to process and render the raw binary data into a viewable image format.

3. Step-by-Step Solution
Step 1: Converting Binary to Image via CyberChef
Copied the entire string of binary digits from the challenge file.

Pasted the text into CyberChef.

Applied the "From Binary" recipe followed by rendering it, or used binary-to-image conversion operations to reconstruct the visual data hidden within the stream.

Step 2: Extracting the Flag
Once CyberChef rendered the binary data, an image appeared revealing the flag visually inscribed inside it. To ensure accuracy and avoid transcription errors:

Used an Image-to-Text (OCR) converter tool on the generated image.
Extracted the resulting text string to uncover the exact flag format.

4. The Flag
**academy{h1dd3n_1n_th3_b1n4ry_1b150ee9}**

5. Key Takeaways
Data Representation: Data isn't always what it looks like at face value; long streams of text or numbers can often be visual structures (like bitmaps or rendered images) in disguise.

Tool Efficiency: CyberChef is an invaluable Swiss-army knife for quick data transformations during CTF forensics challenges.
