# **Finding Lane Lines on the Road** 

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[pipeline]: ./out/design/Pipleline.png "Pipeline"
[step_output]: ./out/step_outputs.png "Step Output"
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps:

![alt text][pipeline]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function as follows:

- At first, slope and intercept is calculated
- Based on slope, lines are separated as left (negative slope) and right (positive slope) lines. Some lines having extreme slope were filtered out to reduce noise.
- Average slope and intercept are calculated for both left and right lines
- Average fit line is calculated from line equation

Sample output from each step:
![alt text][step_output]


### 2. Identify potential shortcomings with your current pipeline

- It worked almost perfect for straight roads, but not very well for curved roads as in challenge video.
- The threshold slope to filter out lines is empirical. So overlay lane lines is sometimes not matching actual line in challenge video.
- Was NOT tested with varying lighting condition, shadow, reflection etc, it may not work well for those cases.

### 3. Suggest possible improvements to your pipeline

- Rather than straight line, the overlay lane line should be improved with curvature based line.
- To adapt with lighting condition etc, color detection (like white/yellow mark) might give better result.
