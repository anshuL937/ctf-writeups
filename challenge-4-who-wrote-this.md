# Challenge 4: Who Wrote This?

**Category:** OSINT / Username pivoting (Basic, 100 points)
**Goal:** Identify the author of a poem from a recovered fragment.
**Flag format:** `DYPU{Author_Name}`
**Flag:** `DYPU{REDACTED}`

## Approach

1. **Collected pivots from the fragment.** The image contained the end of a poem and a chat between two users, `SilasReads` and `MilesCarter`. The chat gave three leads: search the exact last line, the full poem is in "an old writing archive", and SilasReads will ask about it on Reddit under the same username.

2. **Searched the exact last line and rejected a decoy.** Google returned only a loosely similar quote attributed to Dr. Seuss. It was a different line, so a normal search was a dead end.

3. **Pivoted to Reddit.** User `u/SilasReads` had a post asking whether anyone recognised the poem. It said the full piece was preserved by an independent writing archive called **ArchiveQuill**, kept "somewhere developers usually keep public projects", meaning GitHub.

4. **Pivoted to GitHub.** Searching GitHub users for ArchiveQuill found a profile describing itself as an independent literary archive, with one public repository containing the poem.

5. **Verified.** The repository README contained the complete poem. Its last three stanzas matched the recovered fragment word for word, and it ended with a "Written by" credit. Formatted the name as `DYPU{First_Last}`, submitted and accepted.

## Lessons

- People reuse usernames across platforms. One handle can lead through several sites.
- Clues phrased as riddles ("where developers keep public projects") usually point to a specific platform.
- A near-match is not a match. Confirm the text word for word.
