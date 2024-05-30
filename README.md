Background subtraction and blob detection using OpenCV 

eliminating the background from a video by extracting the moving foreground from the static background 
identifies foreground blobs and draws a red circle around them by identifying connected regions in binary images. 

We use the MOG2, simpleblobdetector, drawkeypoints, GaussianBlur, imshow, waitkey, and videocapture method in opencv to preform this operation##

Background subtraction is a technique for separating out foreground elements from the background and is 
done by generating a foreground mask. This technique is used for detecting dynamically moving objects 
from static cameras. Background subtraction techniques are important for object tracking. 

Uses include (object segmentation, security enhancement, and pedestrian tracking) 




