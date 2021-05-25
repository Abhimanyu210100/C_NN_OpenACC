# C & NN OpenACC

Convolution plus Neural Network written in C/C++ and parallelised in OpenACC

## **Dataset:**
The dataset was taken from NIST Ultra High Carbon Steel Micrographs. 6 images were extacted from each image in the data set and it is available in the given drive link.
https://drive.google.com/file/d/1ghYcp5nsUYo9bgHaRmfRKr-cAlzyJClr/view?usp=sharing
Labels are provided in the folder 'nist_dataset'

## **Task:** 

Classifying SEM images of microstructures into 7 different categories.

## **Model Architecture:**
- Sobel Kernel was used for edge detection on images along the verticle and horizontal direction
- Standard sharpen kernel was used to increase the contrast between the edge detected in a lower dimension representation of the image
- Convoluted Neural Network: Softmax function is used to compute the belongingness to a particular class. Cross-Entropy loss function is used to compute the loss for a multi-class classification problem

## **Image Preprocessing:**

Each image from the NIST dataset is converted to 6 images (each of 256x256 pixels). Therefore, the final dataset contains 5766 images. These images were processed using the Sobel and Sharpen kernels and the final image was stored as a CSV which is used to train the model.

## **Labels:**

This is a 7 class classification problem and one hot encoding has been used for the labels.

## **Libraries Used:**

No libraries apart from the in-built C libraries were used. 

## **Implementation:**
*The code shown below was run and tested on AQUA computing cluster*

The images must be saved in the folder named 'image_csv_files' present at the same level as convNetV1.c.

To run the Neural Network in parallel OpenACC was used. To get a detailed description of the time used per parallel block of the code set `PGI_ACC_TIME=1` else `PGI_ACC_TIME=0`. The command lines below can be used to compile the code in parallel.

```
module load nvhpc-compiler
export PGI_ACC_TIME=1
pgcc -acc -Minfo=accel convNetV1.c
```
