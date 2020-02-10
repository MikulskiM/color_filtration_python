import cv2
import numpy as np

# This function does nothing | it is needed because cv2.createTrackbar() must take function which will start on trackbar change
def nothing(x):
    pass

# Window with trackbars
cv2.namedWindow("Trackbars")
cv2.createTrackbar("lower_H", "Trackbars", 0, 255, nothing)
cv2.createTrackbar("lower_S", "Trackbars", 0, 255, nothing)
cv2.createTrackbar("lower_V", "Trackbars", 0, 255, nothing)
cv2.createTrackbar("upper_H", "Trackbars", 0, 255, nothing)
cv2.createTrackbar("upper_S", "Trackbars", 0, 255, nothing)
cv2.createTrackbar("upper_V", "Trackbars", 0, 255, nothing)

image = cv2.imread('task2_2.png')   # loading an image

# cv2.imread() returns an image in BGR, so we have to convert it to HSV to use it easly
hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)

while True:
#     We check the trackbars positions to get values of lower and upper H, S and V
    lower_h = cv2.getTrackbarPos("lower_H", "Trackbars")
    lower_s = cv2.getTrackbarPos("lower_S", "Trackbars")
    lower_v = cv2.getTrackbarPos("lower_V", "Trackbars")

    upper_h = cv2.getTrackbarPos("upper_H", "Trackbars")
    upper_s = cv2.getTrackbarPos("upper_S", "Trackbars")
    upper_v = cv2.getTrackbarPos("upper_V", "Trackbars")

#     to use all values of H, S and V at the same time we have to make it an array
    lower_hsv = np.array([lower_h, lower_s, lower_v])
    upper_hsv = np.array([upper_h, upper_s, upper_v])

#     we create the mask with our upper and lower HSV values
    mask = cv2.inRange(hsv_img, lower_hsv, upper_hsv)
    
#     our result will be the bitwise AND between original image and our mask (HSV range)
    result = cv2.bitwise_and(image, image, mask=mask)

    cv2.imshow("result", result)
    cv2.imshow("original image", image)
    cv2.waitKey(1)
    # cv2.waitKey()
    # print("lower_H = " + str(lower_h))


cv2.waitKey()
