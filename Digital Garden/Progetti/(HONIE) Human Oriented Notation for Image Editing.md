# Premise

#todo

# File sections

HONIE files are divided in two sections, namely Attributes and edits.

Attributes and Edits sections are separated by three hyphens `-` (ASCII code 45) and a newline character (ASCII code 10).

## Attributes section

the Attributes section contains multiple fields, each followed by `:` (ASCII code 58) and a white-space (ASCII code 32):

1.  `sequence name`: the name of the sequence of edits;
2.  `note`: an optional description of the sequence of edits;
3.  `resources path`: the path of the resources directory, if any image other then the source image is needed.

## Edits section

An edit is the written description of the application of a determined function, which inputs are the output of the previous edit (or the source image in the case of the first edit) and additional arguments; while its output is the transformed image.

Edits are listed in chronological order from the beginning to the end of the file.

Each line in the Edits section can be followed by an hash sign `#` (ASCII code 35)

Edits are written as follows: an empty line, the edit name, followed by `:` and its parameters, each on a new line and preceded by the tabulation character (ASCII code 9).

- If an edit uses only one parameter, its nameless and written just as the parameter value, represented in the appropriate literal for its type.
- Else, if an edit uses multiple parameters, they are written as their name, followed by `:`, a white-space and the parameter value.

## Parameter types

- **Increment**: represents a positive or negative increment of the image property intensity described by the parameter. The numerical value is preceded by a plus or a minus.
  Example: `-10`
- **Angle**: represents a positive or negative increment of the image property intensity described by the parameter; used for properties which show the same behaviour every 360 increments. The numerical value is preceded by a plus or a minus and followed by `°`.
  Example: `+60°`
- **Kelvin**: represents a temperature in Kelvin degrees, bounded from 1000K to 40000K. The numerical value is followed by an uppercase K.
  Example: `4000K`
- **Pixels**: represent a length in pixels. The numerical value is followed by px.
  Example: `2px`
- **Percentage**: represents a portion in 1/100 increments bounded between 0 and 100. The numerical value is followed by a percentage sign `%` (ASCII code 37).
  Example: `25%`
- **Axis**: represents whether the property is shown along the vertical or horizontal axis. The axis literals are either `horizontal` or `vertical`.
- **Color**: represents a color value in the RGB color space. Its literal is either a tuple in the format `RGB(r, g, b)` or, preferably, the corresponding color literal if any.
- **Image**: represents the image file using its relative path from the resources folder.
- **String**: represents a mode for a parameter with multiple modes.
  Example: `multiply`

## Example

```
sequence name: Test Sequence
note: A demonstrative sequence
resources path: resources/
---

brightness: +10

hue: -25°

image overlay:
	image: checkboard.png
	mode: multiply
	opacity: 50%

flip: horizontal

color overlay:
	color: RGB(10, 50, 200)
	mode: average
	opacity: 10%
```

# Edits list

- flip (axis)
- brightness (increment)
- contrast (increment)
- saturation (increment)
- hue rotation (angle)
- temperature (kelvin)
- rotate (angle)
- noise:
	- grain size (pixels)
	- contrast (increment)
	- opacity (percentage)
- overlay color:
	- mode (string)
	- opacity (percentage)
	- color (color)
- overlay image:
	- mode (string)
	- opacity (percentage)
	- path (image)
- overlay gradient:
	- mode (string)
	- opacity (percentage)
	- color 1: (color)
	- color 2: (color)
	- (optional) color 3: (color)
	- ...
	- (optional) color n: (color)

#todo 

- exposition
- add frame
- add text 
- denoise 
- gaussian blur 
- blur around point 
- vignette
- crop (origin point in center + aspect ratio)
- upscale
- downscale

# Materiale di studio

(https://upf.hal.science/hal-03132309v1/document)

https://www.formdev.com/flatlaf/

https://stackoverflow.com/questions/603283/what-is-the-best-java-image-processing-library-approach

- flip:
	- args: (string) "vertical" or "horizontal"
	- description: flips the image vertically or horizontally:
- brightness:
	- args: (increment) the 1/256 brightness increment
	- description: adds 1 to every color channel
- contrast: (https://math.stackexchange.com/questions/906240/algorithms-to-increase-or-decrease-the-contrast-of-an-image)
	- gain (number)
	- ~~bias (number)~~
- saturation (https://changingminds.org/explanations/perception/visual/hsl.htm#:~:text=the%20Luminosity%20of%20a%20pixel,(2%20%2D%20max%20%2D%20min)):
	- args: increment
- hue shift (https://stackoverflow.com/a/8510751) (https://stackoverflow.com/questions/8507885/shift-hue-of-an-rgb-color)
	- args: degree
- temperature (https://stackoverflow.com/questions/11884544/setting-color-temperature-for-a-given-image-like-in-photoshop) (https://photo.stackexchange.com/a/122262)
	- args: increment
- rotation (https://www.reddit.com/r/algorithms/comments/rvvktf/how_to_do_image_rotations/)
	- args: degrees
	- rotates the image (transparent background)
- noise (intensity, size, contrast)
- denoise:
	- algorithm name
	- parameters
- gaussian blur
- gaussian blur around a point
- vignette around a point
- overlay (image, mode, intensity)
- frame:
	- args: color, width, rounded corners
- color filter
- gradient filter:
	- args:
		- direction: vertical, horizontal, degrees from horizontal
		- color 1:
		- color 2:
		- ...
		- color n:
- crop