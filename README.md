# ImageSegmentation-SartorLab
## Overview
This project was started in an attempt to improve the tracking of the growth rate of different variations of the Lemna Gibba plant, which is being studied in Dr. Sartor's lab. This process had already been started by Kassidy Robinson, using PlantCV for image segmentation in her script, but we were looking to improve the accuracy using Ultralytics YOLOv8 for image segmentation instead. To start, I used Roboflow to annotate hundreds of Lemna Gibba images produced by Kassidy in the lab, and imported these images as a dataset into my ImageSegmentation.ipynb file, which is the python script that I used for this project. After importing the dataset, I used YOLOv8 with the dataset to train a new model for detecting the plant images. The cell in the ImageSegmentation file for training the model only needs to be ran once, as each time it is ran it will produce a new model. After training this model, it is used to predict and segment a large set of plant images. In our lab, the images are either images of the plant itself, or images of the barcode that correlates to a specific plant which can be determined by the camera number in the file name for the image. The python script seperates these different kind of images into two different folders using the camera number; one called masks for the masked images of the plants and one called barcode_images for the images of the barcodes. These folders can be found in runs/segment/predict*. Each time the script is ran a new predict folder is created with the number following incremented. First the script will iterate through the masked image folder, and detect the area that the plant takes up in the image using the number of white pixels, and writes this information along with other information pertaining to the image to a csv file. Then the script iterates through the barcode images and uses pyzbar to read the barcodes of the images and write this and the other information pertaining to it to the same csv file. After this the script iterates through all the plant images and finds the matching barcode image and writes the information to a new csv file with all the information, including area and barcode, in the same row. After testing the script on smaller sets of images to ensure it worked properly, I ran it on one of our larger sets of images that we also ran o Kassidy's script on so that we could use R to compare our results.

## Technologies Used
**Python**: Python is the primary programming language used in this project for its versatility, extensive libraries, and ease of use.

**Ultralytics YOLOv8**: YOLOv8, developed by Ultralytics, is a state-of-the-art deep learning model for object detection and image segmentation tasks. It provides efficient and accurate results, making it suitable for our project in detecting the Lemna gibba in the images.

**Roboflow**: Roboflow is utilized for data preprocessing tasks such as data augmentation, normalization, and annotation management. We used this to streamline the data preparation process by annotating hundreds of images of the Lemna gibba, ensuring high-quality input data for training the YOLOv8 model.

**R**: R is used for testing and analyzing the segmentation results obtained from the YOLOv8 model. Its statistical and visualization capabilities are leveraged to evaluate the performance of the segmentation algorithm and gain insights from the results.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install ultralytics.

```bash
pip install ultralytics==8.0.28
```
## Contributors
**Kyle Curley**: Annotating images in Roboflow, and writing python script to train and predict with YOLO model, and pull data from images and writing them to a csv file.

**Kassidy Robinson**: Produced plant images used to train model and used her logic for reading barcodes from images. 

**Ryan Sartor**: Overall idea for project and helped with writing R script to compare results of Kassidy's and my data.
