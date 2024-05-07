# WebGL Cube Demo with Perspective Matrix

This repository contains a WebGL implementation of a cube with an application of a perspective matrix to appear in a perspective view.

## Known Issues

The current implementation has an issue where the red face, which is the front of the cube, disappears when the perspective matrix is in use.

## The Perspective Matrix

The main point of this repository is the use of a perspective matrix. The matrix used in this project is the Vulkan perspective matrix, which is defined as follows:

```javascript
const vulkanPerspectiveMatrix = [
    1/((w/h)*(Math.tan(vulkanTheta/2))), 0, 0, 0,
    0, 1/(Math.tan(vulkanTheta/2)), 0, 0,
    0, 0, far/(far-near), ((-far)*(near))/(far-near),
    0, 0, 1, 0
]
```

Where:
- `w` and `h` are the width and height of the canvas.
- `near` and `far` define the near and far spectrum of the z-axis.
- `vulkanTheta` is the field of view (FOV) angle.

This matrix can be converted into a more readable format as follows:

$$
\begin{bmatrix}
\frac{1}{{\frac{w}{h} \cdot \tan\left(\frac{{vulkanTheta}}{2}\right)}} & 0 & 0 & 0 \\
0 & \frac{1}{{\tan\left(\frac{{vulkanTheta}}{2}\right)}} & 0 & 0 \\
0 & 0 & \frac{{far}}{{far-near}} & \frac{{-far \cdot near}}{{far-near}} \\
0 & 0 & 1 & 0 \\
\end{bmatrix}
$$

## Learning Resources

Most of the knowledge about the matrix used in this project came from a [YouTube video](https://youtu.be/U0_ONQQ5ZNM?si=87EWVEHGwkfG2oK7). This video provides a comprehensive explanation of the perspective matrix and its application in 3D graphics. It's a great resource for anyone looking to understand the underlying mathematics of 3D transformations.
