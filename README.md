# CTF Write-ups

Step-by-step write-ups of CTF challenges I solved, focused on **methodology**: how I found each lead, which leads I rejected, and how I verified the answer before submitting.

> Flags are redacted (`DYPU{REDACTED}`). These challenges come from a university Ethical Hacking assessment, and I don't want to spoil them for future students.

| # | Challenge | Category | Key techniques |
|---|-----------|----------|----------------|
| 1 | [Cozy vibes!!!](challenge-1-cozy-vibes.md) | OSINT / Geolocation | EXIF analysis, reverse image search, landmark cropping, Street View verification |
| 2 | [Is that the GOAT...](challenge-2-is-that-the-goat.md) | OSINT / Geolocation | Reverse image search, source verification, answer-format matching |
| 3 | [Hidden in Plain Sight](challenge-3-hidden-in-plain-sight.md) | Digital Forensics / Steganography | LSB steganography, PNG analysis, CyberChef |
| 4 | [Who Wrote This?](challenge-4-who-wrote-this.md) | OSINT / Username pivoting | Exact-phrase search, Reddit and GitHub pivoting |
| 5 | [Behind the Address](challenge-5-behind-the-address.md) | OSINT / Web | HTML source review, SHA-256 hashing, Gravatar lookup, Base32 decoding |

## What these show

- **Verifying, not guessing.** Several challenges had decoy leads (a wrong town with the same name, a similar but different quote). Each write-up shows how I spotted and rejected them.
- **Understanding why a technique works.** For example, why a lossless 8-bit PNG preserves least-significant bits, or why Gravatar can be looked up from a hashed email.

## Tools used

`exiftool` · CyberChef · Google Lens · Google Maps Street View · browser dev tools · Gravatar API

---
*Author: Anshul More, B.Tech Computer Science & Engineering (Cybersecurity), Ramrao Adik Institute of Technology*
