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
- **Name:** VIGNESH M  
- **Register Number:** 212223240176

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
img = cv2.imread('Eagle_in_Flight.jpg',0)
```

#### 2. Print the image width, height & Channel.
```python
print(img.shape)
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img[:,::-1],cmap='gray')
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
bgr_image = cv2.imread('Eagle_in_Flight.jpg')
cv2.imwrite('output_image.jpg', bgr_image)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
saved_img = cv2.imread("output_image.jpg")
rgb_image = cv2.cvtColor(saved_img,cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(rgb_image)
print(rgb_image.shape)
plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
croped_image = rgb_image[20:430,200:550]
plt.imshow(croped_image)
```

#### 8. Resize the image up by a factor of 2x.
```python
resized_image = cv2.resize(rgb_image,None,fx=2,fy=2,interpolation=cv2.INTER_CUBIC)
plt.imshow(resized_image)
```

#### 9. Flip the cropped/resized image horizontally.
```python
crop_flipped = cv2.flip(croped_image,1)
plt.imshow(crop_flipped)
plt.title("Flipped crop image")
plt.show()
resize_flipped = cv2.flip(resized_image,1)
plt.imshow(resize_flipped)
plt.title("Flipped resized image")
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
apollo_img = cv2.imread("Apollo-11-launch.jpg")
plt.imshow(apollo_img)
plt.show()
print(apollo_img.shape)
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
# YOUR CODE HERE: use putText()
text_image = cv2.putText(apollo_img,text,(240,680),cv2.FONT_HERSHEY_COMPLEX,1.2,[250,190,10],3,cv2.LINE_AA)
plt.imshow(text_image)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
# rect_color = magenta
rect_image = cv2.rectangle(apollo_img,(500,630),(750,60),(255,0,255),3)
```

#### 13. Display the final annotated image.
```python
plt.imshow(rect_image)
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python
boy_img = cv2.imread('boy.jpg')
plt.imshow(boy_img[:,:,::-1])
plt.show()
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
matrix_ones = np.ones(boy_img.shape,dtype='uint8') * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(boy_img, matrix_ones)
img_darker = cv2.subtract(boy_img, matrix_ones)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(14,4))
plt.subplot(1,3,1); plt.imshow(cv2.cvtColor(boy_img,cv2.COLOR_BGR2RGB)); plt.title("Original Image"); plt.axis('off');
plt.subplot(1,3,2); plt.imshow(img_brighter[:,:,::-1]); plt.title("Brighter Image");plt.axis('off');
plt.subplot(1,3,3); plt.imshow(img_darker[:,:,::-1]); plt.title("Darker Image");plt.axis('off');
plt.show();
```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
img_higher1 = cv2.convertScaleAbs(boy_img, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(boy_img, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(15,5))
plt.subplot(1,3,1); plt.imshow(cv2.cvtColor(boy_img,cv2.COLOR_BGR2RGB)); plt.title("Original Image");plt.axis('off');
plt.subplot(1,3,2); plt.imshow(cv2.cvtColor(img_higher1,cv2.COLOR_BGR2RGB)); plt.title("Lower contrast Image"); plt.axis('off');
plt.subplot(1,3,3); plt.imshow(cv2.cvtColor(img_higher2,cv2.COLOR_BGR2RGB)); plt.title("Higher contrast Image"); plt.axis('off');
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b,g,r = cv2.split(boy_img)
plt.figure(figsize=(15,5))
plt.subplot(1,3,1); plt.imshow(b,cmap='gray'); plt.title("Blue Channel"); plt.axis('off'); 
plt.subplot(1,3,2); plt.imshow(g,cmap='gray'); plt.title("Green Channel"); plt.axis('off'); 
plt.subplot(1,3,3); plt.imshow(r,cmap='gray'); plt.title("Red Channel"); plt.axis('off'); 
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_img = cv2.merge([r,g,b])
plt.imshow(merged_img)
plt.title("Merged Image")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
boy_hsv = cv2.cvtColor(boy_img, cv2.COLOR_BGR2HSV)
h,s,v = cv2.split(boy_hsv)
plt.figure(figsize=(15,5))
plt.subplot(1,3,1); plt.imshow(h,cmap='gray'); plt.title("Hue"); plt.axis('off'); 
plt.subplot(1,3,2); plt.imshow(s,cmap='gray'); plt.title("Saturation"); plt.axis('off'); 
plt.subplot(1,3,3); plt.imshow(v,cmap='gray'); plt.title("Value"); plt.axis('off'); 
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.merge([h,s,v])
plt.figure(figsize=(15,5))
plt.subplot(1,2,1)
plt.imshow(boy_img[:,:,::-1])
plt.axis('off')
plt.title("Original Image")
plt.subplot(1,2,2)
plt.imshow(merged_hsv)
plt.title("Merged HSV Image")
plt.axis('off')
plt.show()
```

## Output:
- **i)** Read and Display an Image
- <img width="515" height="321" alt="Untitled" src="https://github.com/user-attachments/assets/2a790bb7-042e-4b94-9d33-56793228933c" />
<img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/f8af40fe-5041-4d4b-b86e-642d87c49abe" />
<img width="515" height="321" alt="Untitled" src="https://github.com/user-attachments/assets/da474bca-8a8d-4efb-b01b-385223d7ef97" />
<img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/ae2cd866-5733-49ea-8ce8-db987a3fffc0" />
7aea9db66ae" />
<img width="515" height="321" alt="Untitled" src="https://github.com/user-attachments/assets/0e0cf2a6-9adc-464f-8329-43fd42ea6886" />




- - **ii)** Modify Image Contrast.
<img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/e707397e-60b6-4801-90bc-f1d33b2673eb" />
<img width="515" height="321" alt="Untitled" src="https://github.com/user-attachments/assets/b0e10f56-0df7-4993-ae37-a595c7dd7fb9" />
<img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/fa1eed14-feb1-42f3-a4d4-d7162ae71284" />
<img width="515" height="321" alt="Untitled" src="https://github.com/user-attachments/assets/7fb55a87-f038-425b-921e-18dc670ea3f5" />
<img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/80b2b130-f1ad-4165-9be3-a0be585f0ad3" />



- **iii)** Generate Third Image Using Bitwise Operations.
- <img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/47f81174-a661-499a-94ae-c253935963e1" />
- <img width="493" height="411" alt="Untitled" src="https://github.com/user-attachments/assets/5850e864-6011-49c3-9714-c038c7a019fd" />
<img width="389" height="411" alt="Untitled-1" src="https://github.com/user-attachments/assets/db77a653-6ac2-40e8-9c6f-ae83da08c91c" />
<img width="515" height="321" alt="Untitled" src="https://github.com/user-attachments/assets/ce1f55dd-0fa6-421f-8352-f9dbea85dc48" />
<img width="515" height="321" alt="Untitled-1" src="https://github.com/user-attachments/assets/5066ddb8-6d3f-431b-b661-41ae3c4148cd" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

