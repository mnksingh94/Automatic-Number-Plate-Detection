# Automatic-Number-Plate-Detection

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspect](#technical-aspect)
  * [API Call](#api-call-via-postman)
  * [Deployment](#deployment)
  * [Execution](#execution-preparation-and-steps)
  * [Technology Used](#technology-used)
 
 
## Overview
This project is about locating the vehicle number plate and capturing the registration number from there using 
SSD object model and OCR technology.

## Motivation
This model has several use cases like
    - granting access to vehicles based on registration number
    - capturing parking violations
    - maintaining a record of vehicles entering and leaving a parking lot
    
## Technical Aspect 
This project uses SSD object detection model. 

## API call (via postman)

```http
  POST http://127.0.0.1/predict
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `image`   | `string` | `base64 notation of image` |


## Deployment

To deploy this project, please follow the below steps in the same order 

create environment

```bash
  conda create -n <envname> python=3.6 -y
```

activate the environment

```bash
  conda activate <envname>
```

install the requirements file

```bash
  pip install -r requirements.txt
```

create a working directory to hold this project and use the below git commands 
to push work directory contents to your git repo

```bash
    git init
    git add . && git commit -m "first commit"
    git remote add origin https://github.com/.......git
    git branch -M main
    git push origin main
```
    
## Execution Preparation and Steps:

1. Go to GCP platform
    - Create a project like ANPR (for example)
    - Go to Navigation Menu (left hand corner) >> API & Services > Dashboard  
    - Enable API & Services
    - Go/Search for Cloud Vision API and Enable
    - Left side Credentials > Top Create Credentials > Generate API Key and copy this
2. Open the project in pycharm  
    - Go to *rest-server.py* line 64 numberPlateVal = detect_license_plate(ik)
    - Navigate to *detect_license_plate method*  in *getNumberPlateVals.py* line 5 url, replace key= with the current key
    - Start the service via **python rest-server.py**
3. Go to *https://base64.guru/converter/encode/image* and convert selected image to base64 format. 
4. start Postman service
    - POST with json format key "image" and value "base64 encoding of image" to URL *http://127.0.0.1:5000/predict*
    - The output will be base64 string for the cropped portion of the image where the number plate is located 
      and the value of number plate like "numberPlateVal": "HR01MR8022". 
    - This dict – key and value will come after passing thru the OCR
5. In real time when getting data from camera, we do cv2.videocapture and cam.read to get continuous image from the camera.

## Technology Used
<p align="left">

<a href="https://www.python.org" target="_blank"> 
<img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" 
width="40" height="40"/> </a>

<a href="https://keras.io/api/" target="_blank"> 
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Keras_logo.svg/1200px-Keras_logo.svg.png" 
alt="keras" width="40" height="40"/> </a>

<a href="https://www.tensorflow.org" target="_blank"> 
<img src="https://www.vectorlogo.zone/logos/tensorflow/tensorflow-icon.svg" 
alt="tensorflow" width="40" height="40"/> </a>

<a href="https://flask.palletsprojects.com/" target="_blank"> 
<img src="https://www.vectorlogo.zone/logos/pocoo_flask/pocoo_flask-icon.svg" alt="flask" width="40" height="40"/> </a>

</p>

