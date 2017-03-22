## Finding Lane Lines on the Road

### Reflection

#### Describe your pipeline. As part of the description, explain how you modified the `draw_lines()` function.

- pipeline:

1. convert images to grayscale
2. Gaussian blur the image
3. apply Canny to get the edges
4. select the front quadrilateral region to detect lanes
5. apply Hough transform to get lines

- `draw_lines`

There are two lanes we are interested in: the left lane with a
negative slope and the right lane with a positive slope. First I
separate all lines based on their slope: a group of lines with
positive slopes and another group with negative slopes. Then get the
median slope for each group. To get rid of some nosie, filter any
lines with slope value far from the median (use a threshold of
0.1). To reconstruct a single line, I find the top most points for
both lanes, then use the slope values and image height as `y` to
calculate `x` for the bottom points (`(image_size_y - y) / slope +
x`). Finally after we have the 4 points, draw 2 lines on the image.


#### Identify potential shortcomings with your current pipeline

1. the quadrilateral window is customized for the test videos. It's
   not generic.
2. the current `draw_line` only works for straight lanes.
3. the params for Hough transform is not generic
4. it assume both lanes start from the very bottom of an image


#### Suggest possible improvements to your pipeline

I don't know yet.
