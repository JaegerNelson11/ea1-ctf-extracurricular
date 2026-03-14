# Extracurricular Activity Reflection: picoCTF

## Activity Description
To align with my interests in cybersecurity, I participated in picoCTF, a prominent Capture The Flag platform. My focus was on two distinct challenges: Riddle Registry (digital forensics) and Log Hunt (general skills). The objectives were to find hidden flags concealed within a seemingly standard PDF document and scattered across a noisy server log. My expectation was to practice basic forensic extraction and log analysis, but the challenges required a deeper understanding of data encoding, file structures, and command-line text manipulation.

## Technical Decisions
For Riddle Registry, my initial approach of using exiftool to parse standard metadata failed. I pivoted to bypass the PDF format entirely, analyzing the raw binary data. I used the strings command piped into grep. Realizing the flag was encoded, I searched for the Base64 equivalent of the standard flag prefix, successfully locating the target string disguised with an octal \075 pad, and used the base64 utility to decode it.

For Log Hunt, my technical strategy relied entirely on parsing. I used grep to filter a large server log for specific FLAGPART tags. This allowed me to isolate the specific log events leaking the data, which I then manually reconstructed in chronological sequence to form the final flag string.

## Contributions
I completed these activities as an individual contributor. To ensure disciplined project management, I utilized a structured Git workflow. I established a GitHub repository, created separate issues to track each challenges requirements, developed my solutions on isolated feature branches, and merged my documentation and evidence via Pull Requests.

## Quality Assessment
I consider this activity highly successful, but it exposed a blind spot in my initial methodology. My early reliance on high-level tools like exiftool temporarily stalled my progress when the data was deliberately obfuscated. This experience strongly reinforced concepts from my CPT_S 427 Cyber Security coursework, highlighting the reality of data hiding and the importance of understanding encoding formats like Base64. It demonstrated why security professionals must be comfortable analyzing raw file structures and manipulating text using low-level command-line tools.