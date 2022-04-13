Refer to [this](https://medium.com/sysf/bits-to-bitmaps-a-simple-walkthrough-of-bmp-image-format-765dc6857393) for 1, 2, 4, 8, 16 or 24bpp (bits/pixel) bitmap help - doesn't involve alpha channel\
I'll be covering BI_BITFIELDS uncompressed\


Imagemagick by default outputs 32bbp, BI_BITFIELDS, true colour (not palletized, no color table) by default

## Refer to [this](https://en.wikipedia.org/wiki/BMP_file_format)
### File header
  * Offset - from start of file to first byte of pixel array
<hr>
### BITMAPINFOHEADER
Most common DIB header - 40 bytes
  * 1C - bbp - 32
  * 1E - compression method - `BI_BITFIELDS` - alpha channel included - uncompressed - default for 32bbp

Color table - ignore (set to 0 - 4 bytes)\
Important colors - ignore (set to 0 - 4 bytes)\
<hr>
### Bit mask
Following important colors, bit masks are specified\
This is the order in which RGBa data is provided in the pixel array\
Consists of 12 bytes - red, green, blue, alpha\
Location of bit in each byte is where it is found in the pixel\
Default - BGRa
<hr>
Important to note that the pixel array is encoded with data starting from the lower left hand corner of the image
  * Scans left to right
  * Bottom to top
