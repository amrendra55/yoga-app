
# Yoga-Fit : Real Time Pose Estimation App

Created a  yogic pose estimation and correction app which can comprehend asanas performed by the user in real time and provide necessary corrections immediately. The system is designed to be highly accurate and consistent. The ui and experience of the system is  made appealing and the user should recieves a customised report about his training. 

# Dataset

We have total of 4234 labeled images sourced from the internet (Google images + Pinterest). This 
dataset is further divided into 2536 for training and 1698 for testing. The classification according to 
various poses is as follows: 
| Name of Pose | Training Images | Testing Images |
| :---: | :---: | :---: |
|Warrior |400 |418|
|Tree |418 |192|
|Shoulder Stand |168 |208|
|Triangle| 150 |120|
|Dog |400 |180|
|Cobra |400 |232|
|Chair |400 |168|
|No Pose| 200| 180|

# Methodology 

### Preprocessing

1. Get list of pose classes.
2. Skip images which are not RGB.
3. Detect landmarks in each image and write it to the csv files.
4. Get landmarks and scale it to the same size as the input image.
5. Save landmarks if all landmarks above than the threshold.
6. Writing the landmark coordinates to its csv files.
7. Combine all per-csv class CSVs into a sigle csv file.
8. Add the labels.

### Algorithmic Approach

Before being passed to the Neural Network, we use a TensorFlow lite Move net model to find 
skeletal points on the images. This model takes 192 cross 192 image sizes. The model yields 17 
key points namely each having three parameters. Movenet is a bottom up pose estimation model which use heatmap to allocate keypoints. There are 
various classification algorithms Movenet could have used for estimating the keypoints (during its 

training). Cross-validation techniques, such as k -fold cross validation, Monte Carlo cross 
validation, and the Holdout method, are unable to capture as in these methods, both test and 
training data are originated from the same set(population). On the other hand, “leave-one-out cross 
validation” can be used for this problem as it divides data into test and training according to the 
population distribution.
In our project we have used a Deep learning algorithm called as CNN(convolution neural 
network) to feed the flattened feature vector of 17 coordinates(1 dimensional) along with Dropout 
regularization technique to prevent overfitting. Lastly we have used Softmax in the final layer. 
Softmax is a mathematical function that converts a vector of numbers into a vector of probabilities, where the probabilities of each value are proportional to the relative scale of each 
value in the vector.

# Procedural Workflow 

We have developed a web application in which
1. The user first login or sign up with their credentials. 
2. Then the credentials are checked, if correct then user entered in the next interface of our app.
3. Now the next page shows the poses and instructions for how to perform them.
4. User now selects the pose he/she wants to perform and then click on the start video.
5. Now the camera is on and user can see the yoga pose he has to perform on the right side of 
the screen and on the left side user can see him/her performing it.
6. If user performed the correct pose with accuracy more than 80%. Then the pose timer starts 
which shows for how much time user has performed accurately and there is a vest timer 
which depicts the best performance of user in that login session.
7. After that user stop the video then our model will generate the analysis report.
8. Then user can see all the details about the poses he/she performed like accuracy, consistency 
etc.
9. The user has option to log out.