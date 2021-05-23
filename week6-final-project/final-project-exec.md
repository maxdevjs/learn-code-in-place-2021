# Final Project

The final project of Code in Place is meant to be a celebration of what you have learned and a chance to explore one of the joys of coding. For the final project you can also design a program to do whatever you like.

We encourage aesthetic programs, interesting algorithms and code that solves a neat problem. You can chose something that you think is cool. We are providing a couple standard projects in case you have trouble choosing one.

Make any project you like!


<details>
<summary></summary>
<details open>
<summary>Description</summary>

</details>
<details>
<summary>Code</summary>

``
```python
"""
This program takes an image and generates a reflection.
The top half of the generated image is the same as the original.
The bottom half is the mirror reflection of the top half.
"""


from simpleimage import SimpleImage
from random import randint

"""
Filters:

- reflection
- magnify
- vintage
- frame
- rainbow
"""

DEFAULT_FILE = 'images/mt-rainier.jpg'


def make_reflected(filename):
    image = SimpleImage(filename)
    # TODO: your code here.
    width = image.width
    height = image.height
    reflect = SimpleImage.blank(width, height * 2)
    # for y in range(height):
    #     for x in range(width):
    #         pixel = image.get_pixel(x, y)
    #         mirror.set_pixel(x, y, pixel)
    #         mirror.set_pixel((width) - (x + 1), y * 2, pixel)

    for x in range(width):
        #  loop over all the rows from y = 0
        for y in range(height):
            #  your code here
            pixel = image.get_pixel(x, y)
            #  draws original image
            reflect.set_pixel(x, y, pixel)
            #  draws the reflected image
            # R = pixel.red
            # G = pixel.green
            # B = pixel.blue
            # if x > 200 and y > 200:
            #     pixel.red = 0.393 * R + 0.769 * G + 0.189 * B + 255
            #     pixel.green = 0.349 * R + 0.686 * G + 0.168 * B + 25
            #     pixel.blue = 0.272 * R + 0.534 * G + 0.131 * B + 25
            # reflect.set_pixel(x, (height * 2) - (y + 1), pixel)

    """
    frame effect
    vintage
    """
    ratio = 4
    for x in range(width):
        #  loop over all the rows from y = 0
        for y in range(height):
            #  your code here
            pixel = image.get_pixel(x, y)
            #  draws original image
            # reflect.set_pixel(x, y, pixel)
            #  draws the reflected image
            R = pixel.red
            G = pixel.green
            B = pixel.blue
            if 30 < x < width - 30 and 30 < y < height - 30:
                pixel.red = 0.393 * R + 0.769 * G + 0.189 * B
                pixel.green = 0.349 * R + 0.686 * G + 0.168 * B
                pixel.blue = 0.272 * R + 0.534 * G + 0.131 * B

                for i in range(ratio):
                    for j in range(ratio):
                        reflect.set_pixel(x + randint(-7, 7), height + y + randint(-7, 7), pixel)
                    # reflect.set_pixel(x + randint(3, 7), height + y + 3, pixel)
                        # reflect.set_pixel(x - i * j, height + y, pixel)
                reflect.set_pixel(x - 10, height + y, pixel)
                    # reflect.set_pixel(x + 1, height + y + 1, pixel)
    return reflect


def frame(filename):
    image = SimpleImage(filename)
    width = image.width
    height = image.height
    frame = SimpleImage.blank(width, height)
    ratio = 4
    for x in range(width):
        for y in range(height):
            pixel = image.get_pixel(x, y)
            R = pixel.red
            G = pixel.green
            B = pixel.blue
            if 30 < x < width - 30 and 30 < y < height - 30:
                # pixel.red = 0.393 * R + 0.769 * G + 0.189 * B
                # pixel.green = 0.349 * R + 0.686 * G + 0.168 * B
                # pixel.blue = 0.272 * R + 0.534 * G + 0.131 * B

                for i in range(ratio):
                    for j in range(ratio):
                        frame.set_pixel(x + randint(-7, 7), y + randint(-7, 7), pixel)
                frame.set_pixel(x - 10, y, pixel)
    return frame


def noise(filename):
    image = SimpleImage(filename)
    width = image.width
    height = image.height
    noise = SimpleImage.blank(width, height)
    ratio = 4
    for x in range(width):
        for y in range(height):
            pixel = image.get_pixel(x, y)
            R = pixel.red
            G = pixel.green
            B = pixel.blue
            if 30 < x < width - 30 and 30 < y < height - 30:
                # pixel.red = 0.393 * R + 0.769 * G + 0.189 * B
                # pixel.green = 0.349 * R + 0.686 * G + 0.168 * B
                # pixel.blue = 0.272 * R + 0.534 * G + 0.131 * B

                for i in range(ratio):
                    for j in range(ratio):
                        noise.set_pixel(x + randint(-7, 7), y + randint(-7, 7), pixel)
                # noise.set_pixel(x - 10, y, pixel)
    # noise = vintage(noise)
    return noise


"""
absolutely broken :D
"""


def pixelizer(filename):
    image = SimpleImage(filename)
    width = image.width
    height = image.height
    pixelizer = SimpleImage.blank(width, height)
    ratio = 6
    for x in range(width):
        for y in range(height):
            pixel = image.get_pixel(x, y)
            if 30 < x < width - 30 and 30 < y < height - 30:
                if x % ratio == 0:
                    for i in range(ratio):
                        pixelizer.set_pixel(x + i, y, pixel)
                        pixelizer.set_pixel(x, y + i, pixel)
    # pixelizer = vintage(pixelizer)
    return pixelizer


def pixelizer_crazy(filename):
    image = SimpleImage(filename)
    width = image.width
    height = image.height
    pixelizer_crazy = SimpleImage.blank(width, height)
    ratio = 14 # 4
    for x in range(width):
        for y in range(height):
            pixel = image.get_pixel(x, y)
            if 30 < x < width - 30 and 30 < y < height - 30:
                if x % randint(2, ratio) == 0:
                    for i in range(ratio):
                        for j in range(ratio):
                            pixelizer_crazy.set_pixel(x + i, y, pixel)
                            pixelizer_crazy.set_pixel(x, y + i, pixel)
                            pixelizer_crazy.set_pixel(x - i, y, pixel)
                            pixelizer_crazy.set_pixel(x, y - j, pixel)
                            pixelizer_crazy.set_pixel(x, y, pixel)
                            # pixelized.set_pixel(x * ratio + i, y * ratio + j, pixel)
    # pixelizer_crazy = vintage(pixelizer_crazy)
    return pixelizer_crazy


def slicer(filename):
    image = SimpleImage(filename)
    width = image.width
    height = image.height
    sliced = SimpleImage.blank(width, height)
    ratio = 4
    for x in range(width):
        for y in range(height):
            pixel = image.get_pixel(x, y)
            R = pixel.red
            G = pixel.green
            B = pixel.blue
            if 30 < x < width - 30 and 30 < y < height - 30:
                # pixel.red = 0.393 * R + 0.769 * G + 0.189 * B
                # pixel.green = 0.349 * R + 0.686 * G + 0.168 * B
                # pixel.blue = 0.272 * R + 0.534 * G + 0.131 * B

                # if x % ratio == 0 and y % 10 == 0:
                # if x % 10 == 0 and y % 10 == 0:
                # if x % ratio == 0:
                if x % 10 == 0:
                    for i in range(ratio):
                        for j in range(ratio):
                            sliced.set_pixel(x + i, y + j, pixel)
                            # pixelized.set_pixel(x * ratio + i, y * ratio + j, pixel)
    # noise = vintage(noise)
    return sliced


def vintage(filename):
    image = SimpleImage(filename)
    width = image.width
    height = image.height
    vintage = SimpleImage.blank(width, height)
    ratio = 4
    for x in range(width):
        for y in range(height):
            pixel = image.get_pixel(x, y)
            R = pixel.red
            G = pixel.green
            B = pixel.blue
            if 30 < x < width - 30 and 30 < y < height - 30:
                pixel.red = 0.393 * R + 0.769 * G + 0.189 * B
                pixel.green = 0.349 * R + 0.686 * G + 0.168 * B
                pixel.blue = 0.272 * R + 0.534 * G + 0.131 * B

                # if x % 10 == 0:
                vintage.set_pixel(x, y, pixel)
    return vintage


def main():
    # Get file name from user input
    filename = get_file()

    # Show the original image
    # original = SimpleImage(filename)
    # original.show()

    # Show the reflected image
    # reflected = make_reflected(filename)
    # reflected.show()

    # Show the reflected image
    # framed = frame(filename)
    # framed.show()

    # Show the reflected image
    # noisy = noise(filename)
    # noisy = vintage(noise(filename))
    # noisy.show()

    # pixelized = pixelizer(filename)
    # pixelized.show()

    pixelized_crazy = pixelizer_crazy(filename)
    pixelized_crazy.show()

    # sliced = slicer(filename)
    # sliced.show()

    # Show the reflected image
    # vintaged = vintage(filename)
    # vintaged.show()


def get_file():
    # Read image file path from user, or use the default file
    filename = input('Enter image file (or press enter for default): ')
    if filename == '':
        filename = DEFAULT_FILE
    return filename


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />
