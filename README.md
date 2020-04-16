# Hand-Gesture-Recognition Using Python and OpenCv
To recognize hand gestures from a video sequence. To recognize these gestures from a live video sequence, we first need to take out the hand region alone removing all the unwanted portions in the video sequence. After segmenting the hand region, we then count the fingers shown in the video sequence to instruct a robot based on the finger count.
### Find and segment the hand region from the video sequence.
### Count the number of fingers from the segmented hand region in the video sequence.
## Segment the Hand region
The first step in hand gesture recognition is obviously to find the hand region by eliminating all the other unwanted portions in the video sequence.
## Background Subtraction
we need an efficient method to separate foreground from background. After figuring out the background, we bring in our hand and make the system understand that our hand is a new entry into the background, which means it becomes the foreground object.
## Motion Detection and Thresholding
To detect the hand region from this difference image, we need to threshold the difference image, so that only our hand region becomes visible and all the other unwanted regions are painted as black. This is what Motion Detection is all about.
## Contour Extraction
After thresholding the difference image, we find contours in the resulting image. The contour with the largest area is assumed to be our hand.
## Count My Fingers
Having segmented the hand region from the live video sequence, we will make our system to count the fingers that are shown via a camera/webcam.
#### Four Intermediate Steps
1.Find the convex hull of the segmented hand region (which is a contour) and compute the most extreme points in the convex hull (Extreme Top, Extreme Bottom, Extreme Left, Extreme Right).
2.Find the center of palm using these extremes points in the convex hull.
3.Using the palm’s center, construct a circle with the maximum Euclidean distance (between the palm’s center and the extreme points) as radius.
4.Perform bitwise AND operation between the thresholded hand image (frame) and the circular ROI (mask). This reveals the finger slices, which could further be used to calcualate the number of fingers shown.
##### After that, you can use bring in your hand into the bounding box, show gestures and the count of fingers will be displayed accordingly. I have included a demo of the entire pipeline below.
Reference:Hand gesture recoginition using pyhton and OpenCv(gogul Ilango).
