# Image Processing with OpenCV

This project demonstrates various image processing techniques using OpenCV in Python. The code performs the following operations on an image named `A1.jpg`:

1. Reading and Displaying Images
2. Converting to Grayscale
3. Writing Images to Disk
4. Displaying Image Properties
5. Splitting and Merging Channels
6. Resizing Images
7. Extracting Regions of Interest (ROI)
8. Blurring Images
9. Rotating Images

## Requirements

- Python 3.x
- OpenCV library (`cv2`)

Install the required library using pip:


pip install opencv-python



##READ THE IMAGE:


import cv2 as c

# Read the image
img = c.imread("A1.jpg")

# Display the image
c.imshow("IMG", img)
c.waitKey(0)
c.destroyAllWindows()


##GRAY SCALE IMAGE
# Convert to grayscale
grey = c.imread("A1.jpg", 0)
c.imshow("Grey img", grey)
c.waitKey(0)
c.destroyAllWindows()


#WRITE A IAMGE TO THE DISK
# Save normal and grayscale images
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/normalimage.jpg", img)
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/greyimage.jpg", grey)

#SPLITING AND MERGING CHANNELS
# Split the image into its blue, green, and red channels
b, g, r = c.split(img)

# Display each channel
c.imshow("b", b)
c.waitKey(0)
c.imshow("g", g)
c.waitKey(0)
c.imshow("r", r)
c.waitKey(0)
c.destroyAllWindows()

# Save each channel image
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/b.jpg", b)
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/g.jpg", g)
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/r.jpg", r)

#ROI:REGION OF INTREST:
# Resize the image
resize_img = c.resize(img, None, fx=0.8, fy=0.8, interpolation=c.INTER_LINEAR)
print("Resized Shape:", resize_img.shape)

# Display and save the resized image
c.imshow("RESIZE", resize_img)
c.waitKey(0)
c.destroyAllWindows()
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/resizeimg.jpg", resize_img)

##AVERAGE BLUR
# Apply average blur
avg = c.blur(img, (10, 10))
c.imshow("Blur img", avg)
c.waitKey(0)
c.destroyAllWindows()
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/blur.jpg", avg)

#ROTATE THE IMAGE :
# Rotate the image
height, width = img.shape[:2]
center = (width // 2, height // 2)
print("Center:", center)

# Calculate rotation matrix
row_matrix = c.getRotationMatrix2D(center=center, angle=90, scale=0.5)
print("Rotation Matrix:", row_matrix)

# Perform the rotation
rotate_image = c.warpAffine(src=img, M=row_matrix, dsize=(width, height))
c.imshow("ROTATED IMAGE", rotate_image)
c.waitKey(0)
c.destroyAllWindows()
c.imwrite("C:/Users/aedpu/JOSHUA/readed imgs/rotate.jpg", rotate_image)




