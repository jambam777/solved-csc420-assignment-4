Download Link: https://assignmentchef.com/product/solved-csc420-assignment-4
<br>
<ol>

 <li><strong>Stereo Matching Costs </strong></li>

</ol>

(a)  Imagine that two images for stereo matching are captured by the same camera but under different exposure times. Compare the two main cost functions for matching, i.e. SSD and NC, for estimating the correspondences in these two images. Which one performs better and why?




<ol start="2">

 <li><strong>Stereo Matching Implementation – </strong>for​ this question, use the rectified image pair (000020_left.jpg and 000020_right.jpg), the given bounding box in file 000020.txt, and the given parameters in file 000020_allcalib.txt.</li>

</ol>

<ul>

 <li>Write a program to compute the depth for each pixel in the given bounding box of car. Use the algorithm given in class, where given a left patch, compare it with all the patches on the right image’s scanline. To reduce computation complexity, you can try to use a small patch size, or sample patches (e.g. every other pixel) from scanline instead of comparing with all possible patches. Report what is the patch size, sampling method, and matching cost function you used. Use the parameters given and show how depth is computed for each pixel. Also visualize the depth information. Are there any outliers coming from incorrect point correspondences?</li>

 <li>After you compute depth using scanline (above), go to KITTI Stereo 2015 (<a href="http://www.cvlibs.net/datasets/kitti/eval_scene_flow.php?benchmark=stereo">http://www.cvlibs.net/datasets/kitti/eval_scene_flow.php?benchmark=stere</a>​ <a href="http://www.cvlibs.net/datasets/kitti/eval_scene_flow.php?benchmark=stereo">o</a><a href="http://www.cvlibs.net/datasets/kitti/eval_scene_flow.php?benchmark=stereo">)</a><u>​ </u>, and pick a machine learning model from the scoreboard. You can pick a model that comes with code and a pre-trained model so you don’t need to implement yourself. Compute the depth for the whole image using their pretrained model. Compare your results from the previous questions with this results from this model. What is the difference, both in terms of quality and speed?</li>

 <li><strong> </strong>Write​ a short summary of workflow for the model you pick, e.g. what layers do they use, what modules do they use, etc.</li>

 <li> Using the depth information from models, try to determine within the bounding box, which pixel belong to the car based on its distance to the box center pixel’s 3D location (use a threshold). After that, try to determine a 3D bounding box for the car (min &amp; max along X, Y, Z). Visualize the segmentation of pixels within the 2D box, and on another image visualize the 3D box. State the classification threshold for distance.</li>

</ul>

<ol start="3">

 <li><strong>Fundamental Matrix – </strong>for​ this question, take 3 images (I<sub>1</sub>​ ,<sub>​</sub> I<sub>2</sub>​ ,<sub>​</sub> I<sub>3</sub>​ )<sub>​</sub> of an object or a stationary scene as follows: Images I<sub>1</sub>​ ,<sub>​</sub> I<sub>2</sub>​ from almost the same viewpoint, but with a (roll) rotation. That is, take an image (I<sub>1</sub>​ )<sub>​ </sub>, don’t move, but rotate the camera in place around 30-45 degrees, and take another image (I<sub>2</sub>​ ).<sub>​</sub> Take the third image (I​ <sub>3</sub>)<sub>​</sub> from a different viewpoint, e.g. move the camera ~20 cm to the right and rotate (out of plane) to point the camera towards the object again.</li>

</ol>




I<sub>1</sub>​ and I<sub>​ </sub>2​ :<sub>​</sub>




I<sub>1</sub>​ and I<sub>​ </sub>2​ (<sub>​ </sub>top view):




<ul>

 <li><strong>[1 points]</strong> Use SIFT matching (or any other point matching technique) to find a number of point correspondences in the (I<sub>1</sub>​ , I<sub>2</sub>​ )<sub>​</sub> image pair and in the (I<sub>1</sub>​ , I<sub>3</sub>​ )<sub>​</sub> image pair. Visualize the results. If there are any outliers, either manually remove them or increase the matching threshold so no outliers remain. Pick 8 point correspondences from the remaining set for each image pair, i.e. (I<sub>1</sub>​ , I<sub>2</sub>​ )<sub>​</sub> and (I<sub>1</sub>​ , I<sub>3</sub>​ ).<sub>​</sub> Visualize those 8 point matches.</li>

</ul>

It helps in the later steps if the 8 point matches are somewhat distributed over the images rather than being clustered in a small region.




<ul>

 <li><strong> </strong>Using​ what we have learned in class (standard 8-point algorithm) calculate the fundamental matrix F<sub>12</sub>​ for image pair (I<sub>1</sub>​ , I<sub>2</sub>​ <sub>​</sub>) and Fundamental matrix F<sub>13</sub>​ for image pair (I<sub>1</sub>​ , I<sub>​ </sub>3​ )<sub>​ </sub>. (for this question, implement your own standard 8-point algorithm)</li>

</ul>




<ul>

 <li> Using F<sub>12</sub>​ ,<sub>​</sub> calculate the epipolar lines in the right image for each of the 8 points in the left image and plot them on the right image. (for this question you can use any OpenCV functions you want)</li>

</ul>




<ul>

 <li> Using F<sub>12</sub>​ ,<sub>​</sub> rectify I<sub>2</sub>​ with I<sub>1</sub>​ and visualize the resulting image side by side with I<sub>1</sub>​ .<sub>​</sub> Do the same for I<sub>3</sub>​ using F<sub>13</sub>​ .<sub>​</sub> (for this question you can use any OpenCV functions you want)</li>

</ul>




<ul>

 <li><strong> </strong>Using​ OpenCV, compute F’<sub>12</sub>​ and F’​<sub>13</sub> and compare with your results. I.e. are they same? Are they similar? Briefly discuss.</li>

</ul>




<ul>

 <li><strong> </strong>Using​ OpenCV, rectify the images using F’<sub>12</sub>​ and F’<sub>13</sub>​ and<sub>​</sub> compare with your rectifications (part d). Discuss any differences.</li>

</ul>