# Corrupted Witness

**Objective:** We were provided with 8 images (referred to as frames) that were visually very similar to one another. 


### Step 1: Initial Hypothesis & Image Combination
Since I had just successfully solved the "Cold Case" challenge by combining images, my immediate instinct was to apply a similar methodology here. I tried combining the 8 frames using various bitwise operations, hoping a hidden message would emerge. However, this approach did not yield any meaningful results.

### Step 2: Exploring LSB and Corruption Patterns
Realizing simple combination wasn't the intended path, I shifted my focus. I noticed that the images only changed slightly from frame to frame. This led me to two new hypotheses:
1. The hidden data might be encoded in the Least Significant Bits (LSB) of the pixels.
2. The slight changes represented a specific "corruption pattern" that needed to be analyzed across the sequence of frames. 

I spent a considerable amount of time trying to analyze these patterns and extract potential LSB data, but without making tangible progress, I eventually had to pause my efforts on this challenge.

**Author: Krish Barwar**
