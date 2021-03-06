# Panorama-Musaicing
### create panorama image from two scenes


Here we want to create panorama image from two different scenes. this project is consist of 3 main steps : 

- Implementing Harris corner detection algorithm
- Implementing RANSAC algorithm
- Calculating Hemography matrix and mosaicing

our two scenes are shown below : 
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/1.png)
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/2.png)

## Harris corner detection

 Harris is a known algorithm to detect corners of the image. In this method I have used Sobel kernel to get horizental and vertical edges of images to calculate harris response of each pixel and 5*5 gussian filter to smooth image and 0.6 * (largest harris response) as  threshold to determine corners. also I use local non-maxima suppresion to find local maximas. equations of Harris algorithm are below : 
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/formula.png)
result of Harris function on the one of the image is shown : 
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/1_harris.png)

# RANSAC
I have implemented RANSC to find outliers and inliers of correspondeces. this function gets two images and their correspondences points and iteratively chosses 4 random points to calculate H matrix and then computes reprojection error of this H matrix and check it with a threshold to detect inliers. as you can below first image shows correspondence points. in the other images i have specified inliers with green lines and outliers with red lines : 

![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/2_matches.png)
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/2_inliers.png)
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/2_outliers.png)

# Mosaicing
Finally I have used opencv to calculate Hemography matrix between scenes and wrapPrespective function to create panorama image : 
![Alt Text](https://raw.githubusercontent.com/AmirMansurian/Panorama-Musaicing/main/3_combined.png)
