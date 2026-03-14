# Extracurricular Activity Reflection: picoCTF

## Activity Description
To align with my interests in cybersecurity, I participated in picoCTF, a prominent Capture The Flag platform. My main focus was the "Riddle Registry" digital forensics challenge. The objective was to find a hidden flag concealed within the metadata of a seemingly standard PDF document. My expectation was to practice basic forensic extraction, but the challenge required a deeper analysis of data encoding and file structures.

## Technical Decisions
My initial approach was to use exiftool, a high-level command-line application, to parse the standard metadata fields. When this failed to yield the flag, I had to change my strategy. I decided to bypass the PDF file format entirely and analyze the raw binary data. I used the strings command piped into grep. Because searching for plaintext failed, I figured that the flag was encoded. I searched for the Base64 equivalent of the standard flag prefix. This successfully located the target string, which was disguised within an /Author tag using an octal \075 in place of standard Base64 = padding. I then used the base64 terminal utility to decode the final string.

## Contributions
I completed this activity as an individual contributor. To ensure disciplined project management, I utilized a structured Git workflow. I established a GitHub repository, created issues to track the challenge requirements, developed my solution on an isolated feature branch, and merged my documentation via Pull Requests. 

## Quality Assessment
I consider this activity highly successful, but it exposed a blind spot in my initial methodology. My early reliance on high-level tools like exiftool temporarily stalled my progress when the data was purposely obfuscated. This experience really reinforced concepts from my CPT_S 427 Cyber Security coursework. Specifically, it highlighted the reality of data hiding and the importance of understanding encoding formats like Base64. It also demonstrated why security professionals cannot solely rely on automated parsers and must be comfortable analyzing raw file structures using low-level command-line tools. If I were to repeat this event, I would integrate hex editors and raw string analysis earlier in my workflow rather than treating them as a fallback.