# Challenge 5: Behind the Address

**Category:** OSINT / Web (Easy, 200 points)
**Goal:** Starting from a fictional company website, follow the trail to a hidden flag.
**Riddle:** "Every door has a name, and every name leaves a trace… look beyond the company itself."
**Flag:** `DYPU{REDACTED}`

## Approach

1. **Surveyed the website.** A normal-looking IT and cloud company homepage with Services, About, Team and Contact sections.

2. **Found an inconsistency.** In the Team section, one engineer had a placeholder work email (`@nexora.example`). The "Get in touch" box listed a different, personal-style Gmail address for the same first name but a different surname. Mismatches like this are worth following.

3. **Read the page source.** Viewing the source (`Ctrl+U`) and searching for HTML comments (`<!--`) revealed a hidden hint near the footer: *"Some email addresses come with an avatar."* An email that comes with an avatar points to **Gravatar**.

4. **Hashed the email.** Gravatar looks up profiles by a hash of the email address. I computed the **SHA-256** hash of the contact email in CyberChef.

5. **Opened the Gravatar profile.** The hash redirected to a public profile for the same person, listed as a Systems Engineer at the company. The bio ended with an odd string.

6. **Verified with the API.** Gravatar's JSON endpoint (`gravatar.com/<hash>.json`) returned a `hash` field exactly matching my SHA-256, plus the matching name, company and encoded string.

7. **Decoded it.** The string used only `A–Z` and `2–7`, which is the **Base32** alphabet. CyberChef's *From Base32* recovered the flag. Submitted and accepted.

## Lessons

- Always read the page source. Developers leave comments in it.
- Email addresses can be a pivot to public profiles through services that index them by hash.
- Identifying an encoding from its character set (Base32: `A–Z2–7`; Base64: `A–Za–z0–9+/`) saves a lot of guesswork.
