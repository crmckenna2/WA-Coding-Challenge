# WA-Coding-Challenge
Part of Cody McKenna's WA application

## Methodology

  Firstly, my algorithm opens the image and converts it to a tensor. Then it uses a manually coded linear transformation and decision barrier to determine which pixels are orange. If I were to have more time, I would probably use a machine learning method to determine the best parameters for the classifier or just use a SVM. After all, my linear transformation only really detects red pixels. After it determines the (red) orange pixels, it uses gaussian mixture to classify whether each pixel is part of the left or right side lane. Then it uses linear regression to determine an equation for the left and right side of the lane. Finally, it uses the equation to calculate where to draw the lines, draws the lines and saves the results to './answer.png'.

## Libraries Used
  I used three libraries to write this algorithm. The most important one was NumPy, which allowed to compute many things very efficiently. For example, it allowed my to efficiently compute all of the indicies for orange pixels in the image, so that I could use machine learning methods on the orange pixels. Secondly, I used scikit learn for all of my machine learning methods (gaussian mixture and linear regression). Finally, I used PIL for image processing. I regret doing this. I chose it after a few google searches, and it was the first library I found that would allow me to transform a png file to a tensor. Looking back, I would have used OpenCV as it is the main library used by WA and PIL was really slow (out of ~2.7 seconds of total computation, ~2.5 of them were two lines of PIL code).

## What I tried

  There are two notable techniques that I tried that did not end up working. Firstly, I tried to use spectral clustering instead of gaussian mixture to classify which pixels are on a given side of the lane. That was abandoned as it was buggy and slow. Granted, it probably would have worked if I had tuned other parts of code (namely the parameters for the manually coded linear transformation) before clustering. The other technique I was considering adding was using DBSCAN to classify orange objects from the orange pixels and to remove outliers for the linear regression. I believe this would have worked, though it was unnecessary and would add probably decent computation as DBSCAN does not compute centroids for the orange objects. 

## Results

Input Image            |  Output Image
:-------------------------:|:-------------------------:
![](https://github.com/crmckenna2/WA-Coding-Challenge/blob/main/red.png) | ![](https://github.com/crmckenna2/WA-Coding-Challenge/blob/main/answer.png)
