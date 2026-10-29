# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** [POOJA SRI P]  
- **Register Number:** [212224230197]

  ### Ex. No. 01
```.PY
import cv2
import matplotlib.pyplot as plt

print("EXPERIMENT 1: IMAGE HANDLING AND PIXEL TRANSFORMATION USING OPENCV")
print("NAME: POOJA SRI P")
print("REGISTER NUMBER: 212224230197")

img = cv2.imread('pic.jpeg', cv2.IMREAD_COLOR)

if img is None:
    raise FileNotFoundError("Please keep pic.jpeg in the same folder as this notebook.")

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()

height, width = img.shape[:2]
print("Image Shape:", img.shape)

line_img = img_rgb.copy()
cv2.line(line_img, (0, 0), (width - 1, height - 1), (255, 0, 0), 2)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()

circle_img = img_rgb.copy()
cv2.circle(circle_img, (width // 2, height // 2), min(width, height) // 4, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()

rectangle_img = img_rgb.copy()
cv2.rectangle(rectangle_img, (0, 0), (width - 1, height - 1), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()

text_img = img_rgb.copy()
cv2.putText(text_img, "POOJA SRI P", (30, min(100, height - 10)),
            cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 0, 255), 3)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()

image_rgb = img_rgb.copy()

image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis('off')
plt.show()

image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis('off')
plt.show()

image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis('off')
plt.show()

image = img.copy()

print("Pixel value at (100, 100):", image[100, 100])

image[200:min(500, height), 200:min(500, width)] = [255, 255, 255]

image_rgb_modified = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb_modified)
plt.title("Image with White Block")
plt.axis('off')
plt.show()

resized_image = cv2.resize(image, (width // 2, height // 2))
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

print("Resized Image Shape:", resized_image.shape)

plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis('off')
plt.show()

roi = img[50:min(150, height), 50:min(150, width)]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis('off')
plt.show()

flipped_horizontally = cv2.flip(img, 1)
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis('off')
plt.show()

flipped_vertically = cv2.flip(img, 0)
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis('off')
plt.show()

final_image = img.copy()
cv2.line(final_image, (0, 0), (width - 1, height - 1), (255, 0, 0), 2)
cv2.circle(final_image, (width // 2, height // 2), min(width, height) // 4, (0, 255, 0), 5)
cv2.rectangle(final_image, (0, 0), (width - 1, height - 1), (0, 0, 255), 5)
cv2.putText(final_image, "POOJA SRI P", (30, min(100, height - 10)),
            cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 0, 255), 3)

cv2.imwrite('final_modified_image.jpeg', final_image)

print("Final modified image saved successfully as final_modified_image.jpeg")
```

## Output:
<img width="443" height="512" alt="image" src="https://github.com/user-attachments/assets/da7426be-03f8-4f66-b0ea-c6d69dfd3793" />

<img width="460" height="537" alt="image" src="https://github.com/user-attachments/assets/c4a1123d-ad24-4622-bf27-10a28ce17cd9" />
<img width="463" height="532" alt="image" src="https://github.com/user-attachments/assets/92ec6b0f-a6c9-4b77-8694-241fa9834282" />
<img width="473" height="537" alt="image" src="https://github.com/user-attachments/assets/8ad52878-67d4-4756-b015-04df102041b0" />
<img width="533" height="592" alt="image" src="https://github.com/user-attachments/assets/aa789e10-fe27-45e5-aa81-20498a8de4a2" />
<img width="506" height="581" alt="image" src="https://github.com/user-attachments/assets/ec687627-fbe0-4d9a-b5c1-b37b7ce1f9eb" />
<img width="426" height="502" alt="image" src="https://github.com/user-attachments/assets/806a524a-6798-49c2-a990-02e1366bae63" />
<img width="456" height="521" alt="image" src="https://github.com/user-attachments/assets/8f6dbd37-abbd-4b76-9894-df2c38850453" />
<img width="447" height="507" alt="image" src="https://github.com/user-attachments/assets/c22ce424-6745-44bb-9dfb-6409525de94e" />
<img width="477" height="522" alt="image" src="https://github.com/user-attachments/assets/dc94ddf0-77b8-4a93-9258-5938e33c61f0" />
<img width="681" height="513" alt="image" src="https://github.com/user-attachments/assets/107fd068-15b4-4c5a-b200-cd660b01d274" />
<img width="567" height="517" alt="image" src="https://github.com/user-attachments/assets/5bfe971d-8e13-45d4-8fe1-1f0ef075a3db" />
<img width="437" height="497" alt="image" src="https://github.com/user-attachments/assets/3b885b2b-bf63-4247-81d1-1fa86f891e7c" />
<img width="502" height="506" alt="image" src="https://github.com/user-attachments/assets/2fbcbf41-aecc-4a99-881d-4becd4625349" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

