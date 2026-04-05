# Cold Case

## Attempt Summary

Combine two images (`ward_a.png` and `ward_b.png`) to cancel noise.

## Steps

- - XORed both images pixel-by-pixel to eliminate overlapping noise and reveal hidden data

### XOR Script

```python
from PIL import Image
import numpy as np

# Load the two images
img1 = Image.open("ward_a.png").convert("RGB")
img2 = Image.open("ward_b.png").convert("RGB")

# Ensure both images are the same size
if img1.size != img2.size:
    raise ValueError("Images must be the same size for XOR operation")

# Convert images to numpy arrays
arr1 = np.array(img1)
arr2 = np.array(img2)

# Perform XOR operation
xor_arr = np.bitwise_xor(arr1, arr2)

# Convert back to image
xor_img = Image.fromarray(xor_arr.astype("uint8"))

# Save the result
xor_img.save("xor.png")

print("XOR image saved as xor.png")
```

## Result

Produced a clearer image containing the hidden flag.

**Explanation:**

- Each pixel from both images is XORed
- Identical pixel values cancel out (resulting in black)
- Differences reveal the hidden image containing the flag

## Flag

```
psych{41ph4_ch4nn3l_d1d_th3_th1ng}
```
