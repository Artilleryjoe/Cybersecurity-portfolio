# Using ExifTool for Metadata Extraction

## Course  
CYB/550 – Technical Enterprise Security

## Objective  
This lab demonstrates how ExifTool can be used to extract metadata from image files, highlighting potential privacy and security risks associated with embedded data.

## Tools Used  
- ExifTool  
- Sample image files (`.jpg`, `.png`)  
- Kali Linux or equivalent Linux distro

## Procedure  
- Launch the terminal and ensure ExifTool is installed using `exiftool -ver`  
- Create or download an image file to examine  
- Run the command `exiftool image.jpg` to extract metadata  
- Analyze output for sensitive fields such as:  
  - GPS coordinates  
  - Camera make/model  
  - Software version  
  - Date and time  
- Use `exiftool -gps:all image.jpg` to isolate geolocation data  
- Optionally, remove metadata using `exiftool -all= image.jpg`

## Results  
- Extracted full metadata from test image  
- Identified embedded GPS coordinates and timestamp  
- Found device details: Canon EOS 5D Mark III, Adobe Photoshop used  
- Successfully removed all metadata with `exiftool -all=`

## Lessons Learned  
- Metadata can unintentionally expose private information such as location, device type, and timestamps  
- Tools like ExifTool are valuable in forensic analysis and OSINT investigations  
- Best practice is to scrub metadata before uploading images to public platforms  
- Organizations should implement policies for media sanitization to reduce data leakage risk
