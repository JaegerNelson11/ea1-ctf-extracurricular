# Challenge: Riddle Registry (picoCTF)

## Objective
The goal of this challenge was to find a hidden flag within the metadata of a provided PDF file (confidential.pdf).

## Methodology

### Step 1: Standard Metadata Extraction
I initially used exiftool to check the standard PDF metadata fields for the flag.

[Terminal Input]
nelso@JaegerLaptop:/.../riddle-registry$ exiftool confidential.pdf

[Terminal Output]
ExifTool Version Number : 12.76 
File Name : confidential.pdf 
Directory : . 
File Size : 183 kB 
File Modification Date/Time : 2026:03:14 11:52:38-07:00 
File Access Date/Time : 2026:03:14 12:40:04-07:00 
File Inode Change Date/Time : 2026:03:14 11:53:16-07:00 
File Permissions : -rwxrwxrwx 
File Type : PDF 
File Type Extension : pdf 
MIME Type : application/pdf 
PDF Version : 1.7 
Linearized : No 
Page Count : 1

Result: The standard fields did not contain the flag, indicating the information was hidden deeper within the file's raw structure or encoded.

### Step 2: Extracting Raw Strings and Searching for Encoded Data
Knowing that standard parsers missed the flag, I used the strings command to extract all readable text from the raw binary data. Suspecting the flag might be encoded in Base64, I used grep to search for the encoded prefix of "picoCTF{" which is "cGljb0NURnt".

[Terminal Input & Output]
nelso@JaegerLaptop:/.../riddle-registry$ strings confidential.pdf | grep "cGljb0NURnt" 
/Author (cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV9jOGY5MWQ2OH0\075)

Result: I successfully located the encoded string. The \075 at the end represents the octal encoding for the = character, which acts as padding for the Base64 string.

### Step 3: Decoding the Flag
I replaced the octal representation with the standard = padding and piped the string into the base64 --decode command to reveal the plaintext flag.

[Terminal Input & Output]
nelso@JaegerLaptop:/.../riddle-registry$ echo cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV9jOGY5MWQ2OH0= | base64 --decode 
picoCTF{puzzl3d_m3tadata_f0und!_c8f91d68}

## Final Flag
picoCTF{puzzl3d_m3tadata_f0und!_c8f91d68}