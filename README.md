# C & NN OpenACC

Convolution plus Neural Network written in C/C++ and parallelised in OpenACC

Task: Classifying SEM images of microstructures into 7 different categories.

Model Architecture: 
-Sobel Kernel was used for edge detection on images along the verticle and horizontal direction
-Standard sharpen kernel was used to increase the contrast between the edge detected in a lower dimension representation of the image
-Convoluted Neural Network: Softmax function is used to compute the belongingness to a particular class. Cross-Entropy loss function is used to compute the loss for a multi-class classification problem

Image Preprocessing:

Each image from the NIST dataset is converted to 6 images (each of 256*256 pixels). Therefore the final dataset contains 5766 images. These images were processed using the Sobel and Sharpen kernels and the final image was stored as a CSV which is used to train the model.

Labels:

This is a 7 class classification problem and one hot encoding has been used for the labels.

Libraries Used:

No libraries apart from the in-built C libraries were used. 