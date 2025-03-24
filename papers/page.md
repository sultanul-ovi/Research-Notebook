---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Page

## Module 01: Welcome and Image Processing Fundamentals

***

### **Module 1.1: Welcome to Computer Vision**

#### **Why Study Computer Vision?**

* Computer vision is the automation of scene understanding using images or videos.
* It is widely used in fields such as robotics, self-driving cars, medical imaging, augmented reality, and more.
* The world around us is complex and messy, but images provide a wealth of information to interpret and analyze.

#### **Motivating Example: Understanding an Image**

* A real-world example: A cluttered kitchen table image.
* Questions to consider:
  * What objects are in the scene?
  * What time of day is it?
  * Where in the house is this?
  * Can you estimate the temperature outside using clues from the image? (e.g., rhododendron leaves curling in cold temperatures)
* The ability to infer such details from a single image highlights the power of human perception and the challenges in replicating it computationally.
* Images contain an incredible amount of information.
* Humans are very good at solving the problems we still sometimes struggle to get computers to do.

#### **Key Computer Vision Questions**

* If a **robot** were placed in this scene, what would it need to understand?
  * Object recognition
  * Spatial understanding
  * Task-specific actions (e.g., sorting, cleaning, interacting with objects)
  * Depth estimation using cameras and sensors
  * Building a real-time **map** of the environment
* This ties into **Simultaneous Localization and Mapping (SLAM)**, an important concept in robotics that will be explored later in the course.

#### **Technological Advancements in Computer Vision**

**Object Detection & Segmentation**

* **YOLO (You Only Look Once)**: Real-time object detection framework.
* **Facebook’s Detectron & PointRend**: More advanced segmentation models.
* **Segment Anything Model (SAM)**: OpenAI's powerful segmentation model.

**Synthetic Image Generation**

* **CycleGAN**: Style transfer between images (e.g., converting horses to zebras).
* **BigGAN & NVIDIA’s GAN models**: Generation of realistic synthetic faces and scenes.
* **Stable Diffusion & DALL·E**: Generating images from text prompts.

**Applications of Computer Vision**

* **Smartphones**: Face recognition, biometric security.
* **Sports Analytics**: Tracking players, enhancing video broadcasts.
* **Self-Driving Cars**: Object detection, lane tracking, path planning.
* **Augmented Reality (AR) & Virtual Reality (VR)**: Head tracking, scene understanding.
* **Robotics**: Navigation, picking objects, interacting with the environment.
* **Medical Imaging**: Detecting diseases, analyzing scans.

#### **Challenges in Computer Vision**

* **Viewpoint Variation**: The same object appears different from multiple angles.
* **Lighting Conditions**: A scene’s illumination changes drastically.
* **Occlusion & Clutter**: Objects may be partially hidden.
* **Motion Blur**: Fast-moving objects create visual distortions.
* **Uncertainty & Ambiguity**: Interpreting uncertain or incomplete data.

***

### **Module 1.2: Course Logistics**

#### **Course Structure**

The course is divided into three main units:

1. **Images (Modules 1–5)**: Covers fundamental mathematical tools used to process images and identify features between multiple images.
2. **Structure (Modules 6–10)**: Focuses on understanding and reconstructing the 3D world, including light models and cameras.
3. **Modern Applications (Modules 11–14)**: Explores state-of-the-art research topics such as place detection, SLAM (Simultaneous Localization and Mapping), and Convolutional Neural Networks (CNNs).

#### **Course Textbooks (Optional)**

* **Concise Computer Vision** by Reinhard Klette (Introductory).
* **Computer Vision: Algorithms and Applications** by Richard Szeliski (available free online) (Advanced).

#### **Prerequisites**

Students are expected to have familiarity with the following:

* **Algorithms & Data Structures**: Implementation of simple algorithms, object-oriented programming, and Big-O notation.
* **Linear Algebra** (Most Important!): Matrix manipulation, eigenvalues, eigenvectors, and familiarity with concepts like Singular Value Decomposition (SVD).
* **Probability & Statistics**: Gaussian distributions, Bayes Rule, hypothesis testing (Chi-squared test), though these will be covered briefly.
* **Python Programming**: Assignments will be implemented in Python using NumPy and Jupyter Notebooks.

#### **Assignments & Grading**

Grading is divided into three main components:

* **5 Programming Assignments** (50% total, **10% each**)
* **5 Concept-Building Assignments** (20% total, **5% each**, lowest dropped)
* **1 Final Project** (30%)

***

### **Module 1.3: Fundamentals of Image Understanding**

#### **Motivation**

* Understanding how images are represented is crucial for manipulation and analysis.
* Representation of images **defines the operations** that can be applied to them.
* Define fundamental image processing terminology.
* Understand how images are stored, represented, and manipulated in computers.
* Introduce image transformations and processing techniques.

#### **What is an Image?**

* An **image** can be defined in multiple ways, for now, it is **a grid of numerical values**.
* Each **pixel** in an image has an intensity value that represents brightness or color.
* Images can have values in different ranges:
  * **Grayscale images**: Values typically range from **0 to 1** or **0 to 255**.
  * **Color images**: Represented using multiple channels (e.g., **RGB** with red, green, and blue components).

#### **Digital vs. Continuous Images**

* **Continuous images**: Represent an image as a mathematical function where intensity values vary smoothly.
* **Digital images**: Represented as a **discrete** set of pixel values sampled at fixed intervals.

#### **Color Images**

* Color images are **multi-channel**, where each pixel has values for different color components.
* The standard convention used in this course is **RGB (Red, Green, Blue)**.
* Additional types of images:
  * **Multispectral Images**: Contain more than three color channels, including **infrared, X-ray**, etc.
  * **Thermal and Satellite Images**: Used in specialized applications such as weather analysis.

#### **Images as Functions**

* An image can be interpreted as a function **f(x, y)**, where:
  * `x, y` are pixel coordinates.
  * `f(x, y)` represents the **intensity or color value** at that location.
* This function is **discretized** when stored in a computer.

#### **Basic Image Transformations**

* **Brightness Adjustment**: Increasing or decreasing intensity values.
* **Contrast Enhancement**: Stretching the range of intensity values.
* **Flipping and Mirroring**: Swapping pixel values across an axis.
* **Rotation and Scaling**: Transforming coordinates while preserving structure.

#### **Computing Image Statistics**

* **Mean Intensity**: The average brightness of all pixels.
* **Variance**: Measures how pixel intensities are distributed.
* **Histograms**: Used to analyze the distribution of brightness levels.

### **Point Processing vs. Filtering**

#### **Point Processing**

* Operations were applied to **individual** pixels without considering neighboring pixels.
* **Examples**:
  * **Brightness modifications** (addition, multiplication).
  * **Contrast adjustments** (gamma correction, inversion).
  * **Color adjustments** (altering individual RGB channels).

#### **Filtering (Neighborhood Operations)**

* Uses **neighboring pixels** to determine the output of each pixel.
* Required for tasks such as:
  * **Blurring**
  * **Sharpening**
  * **Edge detection**
* Filtering **preserves spatial relationships** in an image.

### **Limitations of Point Processing**

* **Point processing assumes** each pixel is independent.
* **Cannot perform** complex operations such as:
  * **Blurring** (requires neighborhood information).
  * **Relighting** (requires understanding of 3D structure).
* **More advanced techniques** are needed for real-world applications.

***

### **Module 1.4: Filtering**

In the last lecture, we discussed **point processing**, where each pixel was manipulated **independently** without considering its surrounding pixels. However, many real-world **image transformations** require context from **neighboring pixels**. This is where **filtering** comes in.

### **Key Assumption of Point Processing**

* Each pixel is **processed independently**.
* The **context of neighboring pixels is ignored**.
* Works well for **brightness adjustment, contrast enhancement, and color modification**, but fails for more complex operations like **blurring, sharpening, and edge detection**.

Thus, **some image transformations require neighboring pixel information**, which **point processing alone cannot provide**.

**What is Filtering?** **Filtering** involves transforming an image using **multiple neighboring pixels** rather than a single pixel at a time.

> **Definition:** A process where an **input image** is modified by combining **neighboring pixel values** to compute the **output image**.**Example:** Blurring an image requires **combining neighboring pixels** to smooth out details.

#### **Types of Filters:**

1. **Smoothing Filters** (e.g., Mean, Gaussian)
2. **Edge Detection Filters** (e.g., Sobel, Laplacian)
3. **Sharpening Filters** (e.g., High-Pass Filters)
4. **Noise Reduction Filters** (e.g., Median Filter)

### **Mean (Box) Filter - The Simplest Filter**

The **Mean Filter** (also called the **Box Filter**) is the most basic type of smoothing filter. The **mean filter** computes the output pixel by averaging its neighboring pixels. This results in a **smoothing effect**, reducing noise and minor variations in intensity.

#### **Example of a 3×3 Mean Filter**

| Input Pixels | Output Pixel |
| ------------ | ------------ |
| 0, 0, 0      | **0**        |
| 0, 90, 0     | **10**       |
| 0, 0, 0      | **0**        |

#### **Process:**

1. Take a **3×3 grid** of pixel values.
2. Compute the **average** of all pixels in the window.
3. Replace the **center pixel** with this average.
4. Move the **window** across the entire image.

#### **Observations:**

* **Bright regions become less distinct.** Bright regions spread outward due to averaging.
* **Edges and fine details are smoothed out.**
* **Isolated bright pixels fade into the surrounding region.**
* If the window contains mostly zeros, the output remains zero.
* If a bright pixel (e.g., 90) is within the window, the average increases.
* The **larger the window**, the **stronger the smoothing effect**.
* The filter effectively reduces **sharp intensity variations** while preserving the overall structure.

#### **Box Filter Matrix Representation**

A **Mean Filter** can be represented as a **convolution kernel**:

$$
K = \frac{1}{9}
\begin{bmatrix}
1 & 1 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1
\end{bmatrix}
$$

Each pixel in the output image is computed using:

$$
I_{\text{filtered}}(x, y) = \sum_{i=-1}^{1} \sum_{j=-1}^{1} I(x+i, y+j) \cdot K(i, j)
$$

where $I(x, y)$ is the original image and $K(i, j)$ is the filter kernel.

#### **Generalizing the Box Filter**

The **box filter** is a special case of a more **general operation** known as **convolution filtering**. **Key Insight:** Instead of **just averaging**, we can **assign different weights** to each pixel in the neighborhood.

***

### 🎯 **Understanding Convolution Filtering**

#### **🔢 Dot Product & Convolution**

Filtering an image **formally** is a **convolution operation**, which consists of:

1. **Sliding a filter (kernel) over the image**.
2. **Multiplying each kernel value with corresponding pixel values**.
3. **Summing the weighted values** to produce the output.

**Mathematically:**

$$
H(x, y) = \sum_{i=-1}^{1} \sum_{j=-1}^{1} I(x+i, y+j) \cdot K(i, j)
$$

where:

* $I(x, y)$ = input image.
* $K(i, j)$ = convolution kernel.
* $H(x, y)$ = filtered image.

#### **Special Case: Mean Filter**

$$
K = \frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}
$$

This is equivalent to **taking a dot product** between the **image patch** and the **filter kernel**.

### **Filtering as a Mathematical Operation**

* Instead of manually summing and dividing, filtering can be represented using a **dot product**. The **dot product** involves element-wise multiplication of two matrices followed by summation. A mean filter can be represented as a **3×3 matrix filled with** `1/9` **values**, making computation uniform.

**Generalizing Beyond Box Filtering:** The box filter is a special case of a **linear shift-invariant (LSI) filter**. More complex filters modify pixel values based on different weights instead of a uniform average.

### **Linear Shift-Invariant (LSI) Filtering**

* **Definition**: The output of a pixel is a **linear combination** of nearby input pixels.
* The **kernel** (a small matrix) determines how much each neighboring pixel contributes to the final value. The kernel **moves across the image** (convolution) to process all pixels.

### **Convolution vs Correlation**

* **Correlation**: A kernel is applied directly to an image.
* **Convolution**: Similar to correlation, but the kernel is **flipped** before application.
* In computer vision, **convolution is preferred** due to its mathematical properties.

### **Separable Filters**

* **Definition**: A filter is separable if it can be **decomposed** into two **1D filters**.
* Example: A **3×3 box filter** can be split into a **1×3 row filter** and a **3×1 column filter**.
* **Why is this useful?**
  * **Computational efficiency**: A 2D convolution requires **N²M²** operations, while two 1D convolutions only require **2NM²**.
  * Many important filters (e.g., **Gaussian blur**) are **separable**.

***

### **Types of Filters**

#### **1. Identity Filter**

* A **trivial filter** where the output is identical to the input image.
* **Kernel**: A matrix with a `1` at the center and `0`s elsewhere.

$$
\begin{bmatrix}
0 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 0
\end{bmatrix}
$$

#### **2. Right Shift Filter**

* Moves the image to the right by one pixel.
* Can be constructed by shifting an identity filter’s kernel.

$$
\begin{bmatrix}
0 & 0 & 0 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{bmatrix}
$$

#### **3. Sharpening Filter**

* Emphasizes **edges** and **fine details** while preserving smooth regions.
* Constructed by subtracting a **smoothed image** from a **scaled original** image.

$$
\begin{bmatrix}
0 & -1 & 0 \\
-1 & 5 & -1 \\
0 & -1 & 0
\end{bmatrix}
$$

**Sharpening Example**

* **Original Image** → **Blur Image** → **Subtract from Original** → **Sharpened Image**
* **Drawback**: Oversharpening can introduce **halo effects** and artifacts.

#### **4. Gaussian Blur**

* A **Gaussian Blur** is a **smoothing filter** that assigns **higher weight** to the **center pixel** and gradually decreases the weights towards the edges.
* A **natural-looking** blur that smooths images while preserving gradual intensity transitions.
* **Kernel**: Values follow a **Gaussian distribution**, assigning **higher weights** to pixels near the center.

$$
\frac{1}{16}
\begin{bmatrix}
1 & 2 & 1 \\
2 & 4 & 2 \\
1 & 2 & 1
\end{bmatrix}
$$

**Why Use Gaussian Blur Instead of a Box Filter?**

* The **box filter** applies equal weighting, leading to **blocky artifacts**.
* The **Gaussian filter** has a smooth fall-off, producing **softer, natural-looking** blurs.

**Gaussian Filter Properties**

* **Separable**: Can be broken into two **1D filters** (one for rows, one for columns).
* **Controlled by sigma (σ)**:
  * **Small σ** → Sharper image, less smoothing.
  * **Large σ** → More smoothing, stronger blur.

### **Edge Detection Using Derivatives**

* **Edges** represent **rapid intensity changes** in an image.
* Mathematically, this corresponds to **taking derivatives**.

#### **Finite Difference Approximation**

* The discrete **approximate derivative** is computed as:
* Forward Difference: $f'(x) \approx f(x+1) - f(x)$
* Central Difference: $f'(x) \approx \frac{f(x+1) - f(x-1)}{2}$
* This can be implemented using a **convolution filter**.

#### **Sobel Filter**

* A **standard edge detection filter** that combines:
  1. A **Gaussian-like smoothing** operation in one direction.
  2. A **derivative computation** in the perpendicular direction.
* **Horizontal Sobel** detects **vertical edges**.
* **Vertical Sobel** detects **horizontal edges**.

#### **Gradient Magnitude and Direction**

* The **gradient** of an image contains both:
  * **Magnitude**: How strong an edge is.
  * **Direction**: The orientation of the edge.
* Computed as:
* $|G| = \sqrt{G\_x^2 + G\_y^2}$
* $\theta = \arctan(G\_y / G\_x)$

### **Higher-Order Derivatives**

* **Laplace Filter**: Second-order derivative to detect **zero crossings**.
* **Laplacian of Gaussian (LoG)**:
  * First, applies a **Gaussian blur**.
  * Then, applies a **second derivative**.
  * Highlights **sharp transitions** and detects edges robustly.

#### ✅ **Assumptions in Filtering**

1. **Translation Invariance**: Filters are applied uniformly across the image.
2. **Linear Combination**: Output is a weighted sum of the input pixels.
3. **Locality**: The influence of a pixel is **limited to a small neighborhood**.

#### ❌ **Limitations of Filtering**

* **Blurring removes fine details.**
* **Edge detection is sensitive to noise.**
* **Sharpening can introduce artifacts.**
* **Filters cannot perform global transformations (e.g., warping, rotation).**

#### ✅ **Key Takeaways**

* **Filtering processes pixels based on their neighbors.**
* **Convolution is the fundamental operation in image filtering.**
* **Mean, Gaussian, Sobel, and sharpening filters are key image processing tools.**
* **Filtering assumptions define how we process images.**
* **Box filter** (mean filter) smooths images but **retains blockiness**.
* **Gaussian blur** produces **natural-looking** smoothing and is **separable**.
* **Sobel filters** detect **edges** by computing **image gradients**.
* **Higher-order filters** like **LoG** enhance edge detection further.

#### **Final Thoughts**

* **Filtering is fundamental** in computer vision, from **noise reduction** to **feature extraction**.
* **Different filters serve different purposes** (smoothing, sharpening, edge detection).
* **Choosing the right filter** depends on the specific application and desired effect.

***
