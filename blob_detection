#video used for blob detection https://www.youtube.com/watch?v=sXDAO0st2cc

# importing libraries 
import numpy 
import cv2

# Capture frames  from a camera
capture = cv2.VideoCapture(0)


#setting up blob detection
params = cv2.SimpleBlobDetector_Params()

#setting up blob detection parameters
# change threshold 
params.minThreshold = 50
params.maxThreshold = 150
# filter by area
params.filterByArea = True
params.minArea = 50
#filter by circularity
params.filterByCircularity = True
params.minCircularity = .5
#filter by Convexity
params.filterByConvexity = True
params.minConvexity = 0.1
#filter by  inertia
params.filterByInertia = False
params.minInertiaRatio = 0.01
#filter by color
params.filterByColor = True
params.blobColor = 255



#setting up parameter for mog2 algorithm, history tells the algorithm 
#number of frames to use to produce background image.
history = 300

# creating object to enable instances of the algorith we are using for background subtraction
background_subtractor = cv2.createBackgroundSubtractorMOG2(history) 



while(True):
	# read frames
	ret, img = capture.read()

	#apply mask for background subtraction
	fgmask2 = background_subtractor.apply(img)
	
	#bluring video for better tracking
	fgmask2_blur = cv2.GaussianBlur(fgmask2, (5, 5), 0)

	#output video with subtracted background
	cv2.imshow('Original', img)
	cv2.imshow('MOG2',fgmask2)


	#creating a detector with the parameters
	detector = cv2.SimpleBlobDetector_create(params)
	#setting up which algorithm to use for blob detection
	keypoints = detector.detect(fgmask2_blur)
	
	
	#draw detected blobs as red circles.
	#cv2.draw_matches_flags_draw_rich_keypoints ensures the size of the circle
	#corresponds to the size of blob
	im_with_keypoints = cv2.drawKeypoints(fgmask2_blur, keypoints, numpy.array([]), (0,0,255), cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS)
	cv2.imshow("keypoints for MOG2", im_with_keypoints)
	k = cv2.waitKey(1) 
	if k == 27: #press 'esc' to exit
		break

capture.release()
cv2.destroyAllWindows()
