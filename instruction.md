## Image to LCD bitmap

### goal

This tool used to convert gray image into 1 bit depth mask for showing on LCD.


### rule

- Create single html file, include HTML and Javascript, CSS.
- Should compitable with microsoft edge and chrome, nice to compitable with firefox.

### spec

* Upload button, load image file from local.
* Image preview adter user selecte local iamge, scale size to friend with page size.
* Input argument include: Target width and height in pixel, width and height ratio for single LCD bit.
* A box on image preview for target area, support move and scale to selected target area inside image.
* An threshold from 0 to 255 mover for convert image to one bit 1/0, an optional check box for using Dithering, an optioncal check box to revert result 0 and 1, an color picker to pick color used for result 1.
* A convert button, convert or refresh image target area to 1 and 0 and show in result area using rectangle with color selected. using dithering algorithem for conversion instead of threshold only.
* support English and Chinese for page text and button.

