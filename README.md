# Hex2ImageEncoder
Encode a hex dump into the IDAT section of a png file


This is not quite steganography and it doesn't create a malicious payload. The intended purpose is to encode abritary files as an image so that they may be passed in messaging apps or any other service that limits by file type, so the fact the image contains a file is rather obvious. Furthermore, if sent as plaintext, patterns can be seen with the naked eye that suggest things such as language or magic numbers. 

PNG was chosen because it is lossless. Metadata was not chosen because occasionally online services will strip this, destroying the file in the proccess. 

The method used takes a hex dump such as from 'xxd' without newlines and chops this into 2 charactor sections which determines value of a given pixel, alternating between R, G, and B. Transparency is used to determine EOF. Sameness of input and small size can cause greater than 100% effenciency, but still a functional level is achieved for random data. ( this method is labeled 'e' for 'enhanced' ). The decoder for this method is not yet finished.

Alternatively, the hex dump can be encoded into greyscale, which decreasees the effeciency to 30-33%.

TODO

Add the ability to pass filename arguments by commandline, rather than hardcoding names

Add decoder for enhanced full RGB version

Unite files into one driver file

Increase robustness by allowing input hex dump to contain spaces and newlines
