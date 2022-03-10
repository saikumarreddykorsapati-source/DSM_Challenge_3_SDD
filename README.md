## DSM_Challenge_3

# ⛳ Social distancing detection

The main purpose of the Social Distancing Detection System is to enable the process of automating the task of monitoring social distancing using surveillance video. 

Since there are no proper vaccines available for covid-19 complete prevention, social distancing is the only feasible approach to fight against this pandemic.


## 🎥 Demo

Youtube Video Link with Explanation [Click here...](https://youtu.be/6dKbLnG0Or4) 

#### After you run the last line of command,a window eill pop up and after execution of the file a `output.avi` file will be showing up in your directory like this:
![Output avi : ](https://github.com/saikumarreddykorsapati-source/DSM_Challenge_3/blob/main/Documentation/social%20distance%20detection.gif)

## 👨 Author

- [@saikumarreddykorsapati-source](https://github.com/saikumarreddykorsapati-source)



## 💻 Tech Stack

Python, Numpy, OpenCv, Yolov3, Scipy, CNN, Deepsort, Deeplearning Techniques 

## 📚 Documentation

(HLD) High Level Design : [Link - Click here...](https://github.com/saikumarreddykorsapati-source/DSM_Challenge_3/blob/main/Documentation/HLD_1.0v_Social_Distancing_Detection.pdf)

(LLD) Low Level Design : [Link - Click here...](https://github.com/saikumarreddykorsapati-source/DSM_Challenge_3/blob/main/Documentation/LLD_V01_Social_Distancing_Detection.pdf)

Wireframe : [Link - Click here...](https://github.com/saikumarreddykorsapati-source/DSM_Challenge_3/blob/main/Documentation/Wireframe_Doc_Social_Distancing_Detection_v01.pdf)

Architecture : [Link - Click here...](https://github.com/saikumarreddykorsapati-source/DSM_Challenge_3/blob/main/Documentation/Architecture_Social_Distancing_Detection.pdf)

(DPR) Detailed Project Report : [Link - Click here...](https://docs.google.com/presentation/d/19z3kfPl4pIk2pRyc5znnFydVfobt05TLQil4lpxf_CA/edit?usp=sharing)

# For GPU runtime:
You can find my google colab file here. [Social distance detector colab](https://colab.research.google.com/drive/13IzdPCsAo4L613cmBEmrtM-NgSvMukb-?usp=sharing)

## Simple Theory
#### Object detection:

We will be using YOLOv3, trained on COCO dataset for object detection.
In general, single-stage detectors like YOLO tend to be less accurate than two-stage detectors (R-CNN) but are significantly faster.
YOLO treats object detection as a regression problem, taking a given input image and simultaneously learning bounding box coordinates and corresponding class label probabilities.
It is used to return the person prediction probability, bounding box coordinates for the detection, and the centroid of the person.

#### Distance calculation:

NMS (Non-maxima suppression) is also used to reduce overlapping bounding boxes to only a single bounding box, thus representing the true detection of the object. Having overlapping boxes is not exactly practical and ideal, especially if we need to count the number of objects in an image.
Euclidean distance is then computed between all pairs of the returned centroids. Simply, a centroid is the center of a bounding box.
Based on these pairwise distances, we check to see if any two people are less than/close to 'N' pixels apart.

## 📎 Features

1. Real-Time alert:

If selected, we send an email alert in real-time. Use case: If the total number of violations (say 10 or 30) exceeded in a store/building, we simply alert the staff.
You can set the max. violations limit in config (Threshold = 15).
This is pretty useful considering the COVID-19 scenario.
Note: To setup the sender email, please refer the instructions inside 'mylib/mailer.py'. Setup receiver email in the config.

2. Threading:

Multi-Threading is implemented in 'mylib/thread.py'. If you ever see a lag/delay in your real-time stream, consider using it.
Threading removes OpenCV's internal buffer (which basically stores the new frames yet to be processed until your system processes the old frames) and thus reduces the lag/increases fps.
If your system is not capable of simultaneously processing and outputting the result, you might see a delay in the stream. This is where threading comes into action.
It is most suitable for solid performance on complex real-time applications. To use threading:
set Thread = True in the config.

3. People counter:

If enabled, we simply count the total number of people: set People_Counter = True in the config.
4. Desired violations limits:

You can also set your desired minimum and maximum violations limits. For example, MAX_DISTANCE = 80 implies the maximum distance 2 people can be closer together is 80 pixels. If they fell under 80, we treat it as an 'abnormal' violation (yellow).
Similarly MIN_DISTANCE = 50 implies the minimum distance between 2 people. If they fell under 50 px (which is closer than 80), we treat it as a more 'serious' violation (red).
Anything above 80 px is considered as a safe distance and thus, 'no' violation (green).


## 📌 Installation for CPU runtime in Ubuntu

Install my-project in following way :

Download Zip File, then 

Open your terminal, Change directory to where you have downloaded this code, Install python3 if you have not, if installed already then it's ok!

\# Run to create a virtual environment named venv.
```bash 
python3 -m venv venv 
```
\# Run below command to activate your environment!
```bash 
source venv/bin/activate 
```
\# Run below command to install the python dependencies related to this project like opencv,numpy,scipy etc.
```bash 
pip install -r requirements.txt 
```
\# Run the command to run your social distancing detection project
```bash 
time python social_distance_detector.py --input pedestrians.mp4 --output output.avi --display 1 
```
After you run the last line of command,a window eill pop up and after execution of the file a output.avi file will be showing up in your directory as shown in above demo.
 
## ⌛ FAQ

#### What is Yolo v3?
- YOLOv3 (You Only Look Once, Version 3) is a real-time object detection algorithm that identifies specific objects in videos, live feeds, or images. YOLO uses features learned by a deep convolutional neural network to detect an object.
#### What is Euclidean Distance?
- Euclidean Distance represents the shortest distance between two points. Most machine learning algorithms including K-Means use this distance metric to measure the similarity between observations.
#### What is Opencv ?
- OpenCV (Open Source Computer Vision Library) is an open source computer vision and machine learning software library.
#### What is social distance detection ?
- The detection tool was developed to alert people to maintain a safe distance with each other by 
  evaluating a video feed.


