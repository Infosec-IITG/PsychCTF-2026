Where are u really?
**Category:** OSINT

**Objective:** Find the physical location hidden within an image file.

**Methodology:**
1.  **Metadata Analysis:** Images often contain hidden EXIF (Exchangeable Image File Format) data that can reveal device information, timestamps, and geolocation.
2.  **Extraction:** I inspected the provided image file using `exiftool` via the command line (an EXIF viewer works as well). 
3.  **Resolution:** The EXIF data contained embedded GPS metadata. By extracting the latitude and longitude tags, the exact location where the photo was taken was revealed, completing the challenge.
