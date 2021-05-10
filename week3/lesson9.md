# Lesson 9: Images May 7th

<details open>
<summary>Learning Goals</summary>
<br />
Learn how work with images in python 🏟️😍
</details>

 ## Videos

- [x] Intro
- [x] SimpleImage

- [x] Image Examples

<details>
<summary>imageexamples.py</summary>

`imageexamples.py`
```python
"""
This program contains several examples of functions that
manipulate an image to show how the SimpleImage library works.
"""

from simpleimage import SimpleImage


def darker(image):
    """
    Makes image passed in darker by halving red, green, blue values.
    Note: changes in image persist after function ends.
    """
    # Demonstrate looping over all the pixels of an image,
    # changing each pixel to be half its original intensity.
    for pixel in image:
        pixel.red = pixel.red // 2
        pixel.green = pixel.green // 2
        pixel.blue = pixel.blue // 2


def red_channel(filename):
    """
    Reads image from file specified by filename.
    Changes the image as follows:
    For every pixel, set green and blue values to 0
    yielding the red channel.
    Return the changed image.
    """
    image = SimpleImage(filename)
    for pixel in image:
        pixel.green = 0
        pixel.blue = 0
    return image


def compute_luminosity(red, green, blue):
    """
    Calculates the luminosity of a pixel using NTSC formula
    to weight red, green, and blue values appropriately.
    """
    return (0.299 * red) + (0.587 * green) + (0.114 * blue)


def grayscale(filename):
    """
    Reads image from file specified by filename.
    Change the image to be grayscale using the NTSC
    luminosity formula and return it.
    """
    image = SimpleImage(filename)
    for pixel in image:
        luminosity = compute_luminosity(pixel.red, pixel.green, pixel.blue)
        pixel.red = luminosity
        pixel.green = luminosity
        pixel.blue = luminosity
    return image


def main():
    """
    Run your desired image manipulation functions here.
    You should store the return value (image) and then
    call .show() to visualize the output of your program.
    """
    flower = SimpleImage('flower.png')
    flower.show()

    darker(flower)
    flower.show()

    red_flower = red_channel('flower.png')
    red_flower.show()

    grayscale_flower = grayscale('flower.png')
    grayscale_flower.show()


if __name__ == '__main__':
    main()
```
</details>

- [x] Greenscreen

<details>
<summary>greenscreen.py</summary>

`greenscreen.py`
```python
"""
This program shows an example of "greenscreening" (actually
"redscreening" in this case).  This is where we replace the
pixels of a certain color intensity in a particular channel
(here, we use red) with the pixels from another image.
"""

from simpleimage import SimpleImage

INTENSITY_THRESHOLD = 1.6


def redscreen(main_filename, back_filename):
    """
    Implements the notion of "redscreening".  That is,
    the image in the main_filename has its "sufficiently red"
    pixels replaced with pixel from the corresponding x,y
    location in the image in the file back_filename.
    Returns the resulting "redscreened" image.
    """
    image = SimpleImage(main_filename)
    back = SimpleImage(back_filename)
    for pixel in image:
        average = (pixel.red + pixel.green + pixel.blue) // 3
        # See if this pixel is "sufficiently" red
        if pixel.red >= average * INTENSITY_THRESHOLD:
            # If so, we get the corresponding pixel from the
            # back image and overwrite the pixel in
            # the main image with that from the back image.
            x = pixel.x
            y = pixel.y
            image.set_pixel(x, y, back.get_pixel(x, y))
    return image


def main():
    """
    Run your desired image manipulation functions here.
    You should store the return value (image) and then
    call .show() to visualize the output of your program.
    """
    original_stop = SimpleImage('stop.png')
    original_stop.show()

    original_leaves = SimpleImage('leaves.png')
    original_leaves.show()

    stop_leaves_replaced = redscreen('stop.png', 'leaves.png')
    stop_leaves_replaced.show()


if __name__ == '__main__':
    main()
```
</details>

- [x] Mirror

<details>
<summary>Code</summary>

`mirror.py`
```python
"""
File: mirror.py
---------------
This program shows an example of creating an image
that shows an original image and its mirror reflection
in a new image.
"""

from simpleimage import SimpleImage


def mirror_image(filename):
    """
    Read an image from the file specified by filename.
    Returns a new images that includes the original image
    and its mirror reflection.
    Returns the resulting "redscreened" image.
    """
    image = SimpleImage(filename)
    width = image.width
    height = image.height

    # Create new image to contain mirror reflection
    mirror = SimpleImage.blank(width * 2, height)

    for y in range(height):
        for x in range(width):
            pixel = image.get_pixel(x, y)
            mirror.set_pixel(x, y, pixel)
            mirror.set_pixel((width * 2) - (x + 1), y, pixel)
    return mirror


def main():
    """
    Run your desired image manipulation functions here.
    You should store the return value (image) and then
    call .show() to visualize the output of your program.
    """
    original = SimpleImage('burrito.jpg')
    original.show()

    mirrored = mirror_image('burrito.jpg')
    mirrored.show()


if __name__ == '__main__':
    main()
```
</details>

Variants:

<details>
<summary>mirror.py</summary>

`mirror.py`
```python
from simpleimage import SimpleImage
import random


def mirror_image(filename):
    """
    Read an image from the file specified by filename.
    Returns a new images that includes the original image
    and its mirror reflection.
    Returns the resulting "redscreened" image.
    """
    image = SimpleImage(filename)
    width = image.width
    height = image.height

    # Create new image to contain mirror reflection
    mirror = SimpleImage.blank(width * 2, height)

    for y in range(height):
        for x in range(width):
            pixel = image.get_pixel(x, y)
            mirror.set_pixel(x, y, pixel)
            pixel.red = random.randint(pixel.red // (x + 1), pixel.red)
            pixel.green = random.randint(pixel.green // 2, pixel.green * 3)
            pixel.blue = random.randint(pixel.blue // 2, pixel.blue)
            # mirror.set_pixel((width * 2) - (x + 100), y, pixel)
            if x % 2 == 0:
                pixel.red = 0
                pixel.green = 0
                pixel.blue = 0
                mirror.set_pixel((width * 2) -
                    (x + random.randint(100, height)), y, pixel)
            else:
                # mirror.set_pixel((width * 2) -
                    # (x + random.randint(100, height)), y, pixel)
                mirror.set_pixel((width * 2) - (x + 1), y, pixel)

            # Original
            # pixel.blue = pixel.red // 2
            # pixel.blue = pixel.green // 2
            # pixel.blue = pixel.blue // 2
            # mirror.set_pixel((width * 2) - (x + 1), y, pixel)
    return mirror
```
</details>

- [x] Wrapup
- [x] Responsibility

## Assignments Problems

<details>
<summary></summary>
<details open>
<summary>Description</summary>

<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

``
```python

```

``
```yaml

```

</details>
</details>
<hr />

## Optional Worked Examples

- [x]

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/9-Images.pdf)
- [x] [Images](https://codeinplace2021.github.io/pythonreader/en/images/)
