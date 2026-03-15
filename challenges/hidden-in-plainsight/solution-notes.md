# Challenge: Hidden in plainsight (picoCTF)

## Objective
The goal of this challenge was to discover a hidden payload tucked away inside a seemingly ordinary JPG image and extract the flag.

## Methodology

### Step 1: Initial Binary and Metadata Analysis
I started by checking for appended files using binwalk, but the scan only detected standard JPEG data. Since no obvious files were appended, I checked the image metadata using exiftool.

[Terminal Input]
nelso@JaegerLaptop:/.../hidden-in-plainsight$ exiftool img.jpg

[Terminal Output]
ExifTool Version Number : 12.76
File Name : img.jpg
...
Comment : c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9
...

Result: The metadata contained a suspicious Comment field encoded in Base64.

### Step 2: Decoding the Clues
I used the base64 terminal utility to decode the hidden text.

[Terminal Input]
nelso@JaegerLaptop:/.../hidden-in-plainsight$ echo c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9 | base64 --decode ; echo

[Terminal Output]
steghide:cEF6endvcmQ=

Result: The decoded string pointed to a specific steganography tool (steghide) and provided a second Base64 encoded string. I decoded the second string to uncover the exact password.

[Terminal Input]
nelso@JaegerLaptop:/.../hidden-in-plainsight$ echo cEF6endvcmQ= | base64 --decode ; echo

[Terminal Output]
pAzzword

### Step 3: Extracting the Payload
After installing the steghide package, I used it to extract the hidden payload from the image using the password I just discovered.

[Terminal Input]
nelso@JaegerLaptop:/.../hidden-in-plainsight$ steghide extract -sf img.jpg
Enter passphrase: 

[Terminal Output]
wrote extracted data to "flag.txt".

Result: The tool successfully extracted a text file named flag.txt which contains the payload.

## Final Flag
picoCTF{h1dd3n_1n_1m4g3_1c55ccd0}