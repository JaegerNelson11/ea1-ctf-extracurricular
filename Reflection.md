# Extracurricular Activity Reflection: picoCTF

## Activity Description
To align with my interests in cybersecurity, I participated in picoCTF, a well known Capture The Flag platform. My focus was on three distinct challenges: Riddle Registry for digital forensics, Log Hunt for general skills, and Hidden in plainsight for steganography. The expectations were to practice basic forensic extraction and log analysis. To accomplish this, I extracted hidden data from PDF documents, parsed complex server logs, and uncovered payloads embedded within image files. These challenges required a proper understanding of data encoding, file structures, and command line text manipulation.

## Technical Decisions
For the Riddle Registry challenge, my starting approach of using exiftool to parse standard metadata failed. I changed to instead bypass the PDF format entirely, analyzing the raw binary data. I used the strings command piped into grep to search for the Base64 equivalent of the standard flag prefix. I was able to locate the target string disguised with an octal padding and used the base64 utility to decode it.

For Log Hunt, my technical strategy relied completely on parsing. I used grep to filter a large server log for specific FLAGPART tags. This allowed me to isolate the specific log events leaking the data, which I then manually reconstructed in chronological sequence to form the final flag string.

For Hidden in plainsight, I used binwalk to check for appended files, and when that returned no results, I looked into the metadata using exiftool. I discovered a Base64 string in the comment field. Decoding this string twice provided the credentials for steghide, allowing me to use the discovered password to successfully extract the payload from the JPG image.

## Contributions
I completed these challeneges individually. To ensure proper project management, I used a structured Git workflow. I established a GitHub repository, created separate issues to track the requirements of each challenge, developed my solutions on isolated feature branches, and merged my documentation and evidence via Pull Requests.

## Quality Assessment
Overall, I think this activity was a success and gave me very practical hands on experience. Starting with Riddle Registry, I learned quickly that basic parsers like exiftool are not always enough when data is intentionally hidden, forcing me to analyze raw binary strings. Log Hunt was a nice shift into general log analysis, showing me how to efficiently use grep to parse a very noisy server file and piece together fragmented information, and Hidden in plainsight brought those skills together by combining metadata analysis with actual steganography extraction using steghide. If I were to do this again, I would probably use raw string analysis and manual extraction methods earlier instead of trusting surface level file data.
