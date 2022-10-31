# Lane_detection
    Lane line detection is a crucial feature of Self-Driving Vehicles. It's an extremely important step for detection of steering angles and localization on the road. The main goal of this project is to develop a pipeline for identification of lane lines on the Road using a series of images and video streams. This pipeline was also tested with personal stream videos.

## Finding Lane Lines on the Road
Lane line detection is a crucial feature of Self-Driving Vehicles. It’s an extremely important step for detection of steering angles and localization on the road. The main goal of this project is to develop a pipeline for identification of lane lines on the Road using a series of images and video streams.

## Steps Taken (code in Jupyter file) 
1. **Importing useful Packages**
    * numpy
    * matplotlib
    * Some Extra  OpenCV functions 
        `cv2.inRange()` for color selection  
        `cv2.fillPoly()` for regions selection  
        `cv2.line()` to draw lines on an image given endpoints  
        `cv2.addWeighted()` to coadd / overlay two images  
        `cv2.cvtColor()` to grayscale or change color  
        `cv2.imwrite()` to output images to file  
        `cv2.bitwise_and()` to apply a mask to an image

2. **Helper functions** 
    * **Grayscale Image function** 
        * This function converts an image with multiple channels (colors) to a single channel (intensity data).
        * Therefore, the processing is faster and it’s an essential step before the detection of lane edges.
    * **Gaussian blur function**
        * This function filters the noise, provides smoothness and prevents false edge detection.
    *  **Canny edge detection function**
        * This function estimates the gradients of the image and supresses the image to determine potential edges based on the thresholds.
    * **Region of interest (ROI)**
        * This function (ROI) is responsible for filtering regions of interest based previously estimated edges and vertices. In our case, the vertice avoids regions without roads.
    * **Hough transformation**
        * The Hough transform to find lines in an image.
    * **Weighted image**
        * Mixing the lines from hough transformation with the original image. The resulting image is based on the following equation: initial_img * ￿ + img * ￿ + ￿

3. Calculate the x coordinate of the intersection
4. Find points with positive and negative slopes
5. add_slope() , & handle Case of empty arrays in the main Pipeline
6. Plot Polygon from Vertices
7. Plot Image Processing
8. Test images & Results
9. Develop a Lane Detection Pipeline
10. Test on Videos
    * process on Video Stream


## **Challenges**
1. The first challenge was to tune the parameters for the hough transformation.
2. I had some issues with NaNs and Inf while debbuging the main pipeline.
3. The most demanding was to stabilize the lane lines of both video streams.

## Identify potential shortcomings
1. The lane lines are straight and very stable in both video streams, however, the pipeline does not work with the challenging video. I believe that it would be also very difficult to detect the lane lines in medium to extreme environments conditions including shades, reflections, occlusions and diverse weather constraints.

##  Possible improvements to your pipeline
1. Find a robust and stable curvature for the lane detection instead of a straigth of line.
2. Tune the mask color parameters and split white and yellow lane lines for processing the
challenging video.