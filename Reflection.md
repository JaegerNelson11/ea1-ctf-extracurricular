# Extracurricular Activity Reflection: picoCTF

## Activity Description
To align with my interests in cybersecurity, I participated in picoCTF, a prominent Capture The Flag platform. My focus was on three distinct challenges: Riddle Registry (digital forensics), Log Hunt (general skills), and Hidden in plainsight (steganography). The objectives included extracting hidden data from PDF documents, parsing complex server logs, and uncovering payloads embedded within image pixels. These activities required a deep understanding of data encoding, file structures, and command-line text manipulation.

## Technical Decisions
For Riddle Registry, my initial approach of using exiftool to parse standard metadata failed. I pivoted to bypass the PDF format entirely, analyzing the raw binary data. I used the strings command piped into grep. Realizing the flag was encoded, I searched for the Base64 equivalent of the standard flag prefix, successfully locating the target string disguised with an octal \075 pad, and used the base64 utility to decode it.

For Log Hunt, my technical strategy relied entirely on parsing. I used grep to filter a large server log for specific FLAGPART tags. This allowed me to isolate the specific log events leaking the data, which I then manually reconstructed in chronological sequence to form the final flag string.

For the final challenge, Hidden in plainsight, I utilized binwalk to check for appended files. When that returned no results, I examined metadata and discovered a Base64 string in the comment field. Decoding this provided the credentials for steghide, a specialized steganography tool. I decoded a secondary Base64 string to find the password pAzzword and successfully extracted the flag from the pixel data of the JPG image.



## Contributions
I completed these activities as an individual contributor. To ensure disciplined project management, I utilized a structured Git workflow. I established a GitHub repository, created separate issues to track each challenges requirements, developed my solutions on isolated feature branches, and merged my documentation and evidence via Pull Requests.

## Quality Assessment
I consider this activity highly successful, as it provided a comprehensive overview of forensic methodologies. My early reliance on high-level tools like exiftool temporarily stalled my progress, reinforcing the need for a versatile toolkit. This experience strongly supported concepts from my CPT_S 427 Cyber Security coursework, specifically the reality of data hiding and the importance of encoding formats like Base64. It demonstrated why security professionals must be comfortable analyzing raw file structures and manipulating text using low-level command-line tools. If I were to repeat this event, I would integrate raw string analysis and steganography extraction tools earlier in my workflow.