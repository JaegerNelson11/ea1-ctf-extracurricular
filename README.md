# Extracurricular Assignment 01: Cybersecurity CTF

## Overview
This repository contains the deliverable for Extracurricular Assignment 01 (EA-1). The chosen activity was participating in **picoCTF**, a cybersecurity Capture The Flag platform. 

Specifically, this repository documents the analysis and solution for the **Riddle Registry** digital forensics challenge.

## Deliverable Information
* **Activity:** picoCTF
* **Challenge:** Riddle Registry (Forensics)
* **Objective:** Extract a hidden, encoded flag from a provided PDF document (confidential.pdf).

## Repository Contents
* challenges/riddle-registry/: Contains the target PDF file and a detailed solution-notes.md write-up.
* assets/: Contains proof of participation and successful completion screenshots.
* Reflection.md: A critical reflection on the activity, technical decisions, and connections to computer science concepts.

## Instructions to Reproduce
To view the technical solution process:
1. Navigate to the challenges/riddle-registry/ directory.
2. Review the solution-notes.md file for the exact command-line workflow (exiftool, strings, grep, base64) used to extract and decode the hidden flag from the raw binary data.

## Proof of Participation
Below is the evidence of successful participation and completion of the challenge:

**1. Registration:**
![Registration](./assets/Registration.png)

**2. Locating the Encoded String:**
![Finding Encrypted Message](./assets/Riddle-Registry-Finding-Encrypted-Message.png)

**3. Decoding the Final Flag:**
![Decoding Encrypted Message](./assets/Riddle-Registry-Decoding-Encrypted-Message.png)

**4. Challenge Solved:**
![Challenge Complete](./assets/Riddle-Registry-Complete.png)

## Reflection Report
Please review the [Reflection.md](./Reflection.md) file in the root directory for a detailed analysis of the technical approach, individual contributions, and a quality assessment of the experience.