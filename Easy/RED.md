1. download red.png and then using an online metadata identifier, i see that it has a poem??
it goes:
"Crimson heart, vibrant and bold, Hearts flutter at your sight. Evenings glow softly red, Cherries burst with sweet life. Kisses linger with your warmth. Love deep as merlot. Scarlet leaves falling softly, Bold in every stroke."

2. anyways, i use a color picker to see if the image is actually red throughout/same shade since hint 1 tells that it may not be uniform, and yeah, turns out there are a few hues of red scattered in ts.

3. look at the raw_header, it goes:
89 50 4E 47 0D 0A 1A 0A 00 00 00 0D 49 48 44 52 00 00 00 80 00 00 00 80 08 06 00 00 00 C3 3E 61 CB 00 00 00 E7 74 45 58 74 50 6F 65 6D 00 43 72 69 6D 73 6F 6E 20 68 65 61 72 74 2C 20 76 69 62 72 61 6E 74 20 61 6E 64 20 62 6F 6C 64 2C 0A 48 65 61 72 74 73 20 66 6C 75 74 74 65 72 20 61 74 20 79 6F 75 72 20 73 69 67 68 74 2E 0A 45 76 65 6E 69 6E 67 73 20 67 6C 6F 77 20 73 6F 66 74 6C
i thought this would be hex->ascii conversion, but no output.

**This is a steganography problem**
Using zsteg(for PNG and BMP problems): extracts info from LSB(least significant bit)
use the command `zsteg -a red.png`
and you get a huge output, then pick any base64 encoded strings and run them on cyberchef expecting an answer and i did.
`b1,rgba,lsb,xy      .. text: "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="                                                                                        
`b1,rgba,msb,xy      .. file: OpenPGP Public Key
`b2,g,lsb,xy         .. text: "ET@UETPETUUT@TUUTD@PDUDDDPE"
`
after running ts, i get the flag.