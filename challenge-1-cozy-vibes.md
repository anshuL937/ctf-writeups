# Challenge 1: Cozy vibes!!!

**Category:** OSINT / Geolocation
**Goal:** From a 360° street-view image of a small town, find the name of the library the author visited.
**Flag:** `REDACTED`

## Approach

1. **Checked for GPS metadata first.** `exiftool -gps:all` returned nothing, so the location had to be found visually.

2. **Reverse image search on the full image.** Google Lens latched onto a readable *NFU Mutual* shop sign and suggested Picton Terrace, Narberth, Pembrokeshire, Wales.

3. **Rejected a decoy.** Asking for a library near that spot returned a mixed-up answer. The text gave a Narberth, *Wales* address, but the linked place was Narberth Community Library in Narberth, *Pennsylvania, USA*. Its Street View looked nothing like the challenge image. NFU Mutual has branches in most Welsh market towns, so the sign only identified the country, not the town.

4. **Searched the most distinctive landmark instead.** I cropped the search to the white building with a clock tower and arches at the end of the street. Lens now identified Broad Street facing Market Square in **Llandovery, Carmarthenshire, Wales**, with Llandovery Town Hall in the background.

5. **Verified with Street View.** At Market Square, Llandovery, the red house, the clock-tower town hall with its fountain, the blue house and the NFU Mutual shopfront all matched, down to the same parked silver car. That confirms it's the same Street View capture.

6. **Found the library.** The town's library is on Market Square, about a one-minute walk from the matched position. Submitted and accepted.

## Lessons

- A recognisable brand sign narrows down the country, not the exact place. Chain stores repeat across towns.
- Cropping the search to one unique landmark gives far better reverse-image results than searching the whole frame.
- Always confirm a geolocation visually before submitting.
