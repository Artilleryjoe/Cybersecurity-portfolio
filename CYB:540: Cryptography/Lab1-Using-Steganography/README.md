# Using Steganography

## Course  
CYB/540 – Cryptography

## Objective  
This lab demonstrates how to conceal data within image files using steganographic techniques. Steganography adds a covert channel of communication, allowing for secure message embedding that avoids detection through traditional means.

## Tools Used  
- `steghide` (Linux steganography tool)  
- Command-line terminal  
- Image file (`cover.jpg`)  
- Text file (`secret.txt`)  

## Procedure  
- Prepare a text file containing the message to hide:
  ```bash
  echo "This is a hidden message." > secret.txt
- Use ```steghide``` to embed the message into an image file:
    ```bash
    steghide embed -cf cover.jpg -ef secret.txt
- Enter a passphrase when prompted to secure the embedded data
- Verify the image appears unchanged to the naked eye
- Extract the hidden message from the stego-image:
    ```bash
    steghide extract -sf cover.jpg
- Enter the correct passphrase to reveal the hidden message

## Results
- The secret text is embedded into the image file without altering its visible content
- The image remains viewable as normal
- The embedded message is successfully extracted only with the correct passphrase
- Attempts to open the image using standard tools do not reveal the hidden content

## Lessons Learned
- Steganography hides the existence of communication, unlike encryption which merely protects content
- Passphrases help prevent unauthorized extraction of hidden data
- Image-based steganography is an effective method for discreet data transfer
- Security through obscurity alone is not reliable — steganography should be paired with encryption for stronger protection
