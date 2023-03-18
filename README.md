# Foodprint :seedling: Food choices that benefit the planet

This is an object detection model for webcam live videos that calculates the carbon footprint of fruits. 

We built our model based on the neural network Darknet [1] and used YOLOv4 as object detection algorithm due to its speed and accuracy [2]. The basis of our code is taken from a tutorial by TECHZIZOU [3]. We enhanced the model by using an own dataset to train on and added the calculation of the carbon footprint. 

As our code is optimized for Google Colab and Google Drive, copy the files into a folder "foodprint" at your Google Drive and start the Jupyter Notebooks from there with Google Colab. 

We already pretained our model. If you want to adapt the model to your personal needs, you can retrain the model by running the jupyter notebook "retrainmodel.ipynb" with Google Colab. If you just want to use our object detection algorithm and see if your food choices benefit the planet, follow the steps:

:one: Copy all files to a folder "foodprint" in Google Drive

:two: Run the jupyter notebook "foodprint.ipynb" with Google Colab

## Data :bar_chart:

The data we used for training our object detection algorithm contains pre-labeled images of fruits [4]. For adding information of the carbon footprint we used a dataset containing CO₂ information and prepared it according to the needs of our use case [5][6].

## Model :bookmark_tabs:

We customized the YOLOv4 model's parameters to fit the number of classes in our dataset by adjusting the maximum number of batches, steps, and filters. 
``Max_batches`` sets the maximum number of batches for sufficient iterations over the dataset. ``Steps`` determines the learning rate's decrease at 80% and 90% of ``Max_batches``. ``Filters`` indicates the number of filters in the convolution layer and affects a model's computational cost and ability to learn complex image features. 

Our final parameter values were: 
- ``Classes`` = 19
- ``Max_batches`` = 38000
- ``Steps`` = 30400, 43200
- ``Filters`` = 72

We started the training of the model using pre-trained weights of YOLOv4 on up to 137 convolutional layers, which allowed for faster processing time and improved accuracy. 

## Results :eyes:

To detect objects with our model via the webcam we used the code of the tutorial by TECHZIZOU [3][7] and added the feature of displaying the total CO₂ output per kg of the food object detected.

![](img/1.jpg)
![](img/2.jpg)

## References
[1] Bochkovskiy A, Darknet. https://github.com/AlexeyAB/darknet

[2] Bochkovskiy, A, Wang C-Y, Liao H-YM (2020) YOLOv4. Optimal Speed and Accuracy of Object Detection.

[3] Train a custom YOLOv4 detector using Google Colab. https://techzizou.com/train-a-custom-yolov4-detector-using-google-colab-tutorial-for-beginners/

[4] 4: CSE299 (apr 2022): Fruit and Vegetable Dataset. Roboflow Universe, visited on 2023-03-14, Open Source Dataset under CC0 1.0 Universal (CC0 1.0) Public Domain Dedication. https://universe.roboflow.com/cse299/fruit-and-vegetable

[5] Petersson, Tashina; Secondi, Luca; Magnani, Andrea; Antonelli, Marta; Dembska, Katarzyna; Valentini, Riccardo; et al. (2021): SU-EATABLE LIFE: a comprehensive database of carbon and water footprints of food commodities. figshare. Dataset. https://doi.org/10.6084/m9.figshare.13271111.v2

[6] Petersson, T., Secondi, L., Magnani, A. et al. (2021). A multilevel carbon and water footprint dataset of food commodities. Sci Data 8, 127. https://doi.org/10.1038/s41597-021-00909-8

[7] theAIGuysCode, YOLOv4 Object Detection on Webcam In Google Colab. (https://github.com/theAIGuysCode/YOLOv4-Cloud-Tutorial/blob/master/yolov4_webcam.ipynb)
 
