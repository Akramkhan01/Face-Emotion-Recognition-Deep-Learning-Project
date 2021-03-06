# Face-Emotion-Recognition-Deep-Learning-Project

# Problem Statement:
The Indian education landscape has been undergoing rapid changes for the past 10 years owing to the advancement of web-based learning services, specifically, eLearning platforms.

Global E-learning is estimated to witness an 8X over the next 5 years to reach USD 2B in 2021. India is expected to grow with a CAGR of 44% crossing the 10M users mark in 2021. Although the market is growing on a rapid scale, there are major challenges associated with digital learning when compared with brick and mortar classrooms. One of many challenges is how to ensure quality learning for students. Digital platforms might overpower physical classrooms in terms of content quality but when it comes to understanding whether students are able to grasp the content in a live class scenario is yet an open-end challenge. In a physical classroom during a lecturing teacher can see the faces and assess the emotion of the class and tune their lecture accordingly, whether he is going fast or slow. He can identify students who need special attention.

Digital classrooms are conducted via video telephony software program (ex-Zoom) where it’s not possible for medium scale class (25-50) to see all students and access the mood. Because of this drawback, students are not focusing on content due to lack of surveillance.

While digital platforms have limitations in terms of physical surveillance but it comes with the power of data and machines which can work for you. It provides data in the form of video, audio, and texts which can be analyzed using deep learning algorithms.

Deep learning backed system not only solves the surveillance issue, but it also removes the human bias from the system, and all information is no longer in the teacher’s brain rather translated in numbers that can be analyzed and tracked.

I will solve the above-mentioned challenge by applying deep learning algorithms to live video data. The solution to this problem is by recognizing facial emotions.

# Dataset Information:
I have built a deep learning model which detects the real time emotions of students through a webcam so that teachers can understand if students are able to grasp the topic according to students' expressions or emotions and then deploy the model. The model is trained on the FER-2013 dataset .This dataset consists of 35887 grayscale, 48x48 sized face images with seven emotions - angry, disgusted, fearful, happy, neutral, sad and surprised. Here is the dataset link:- https://www.kaggle.com/msambare/fer2013
# Different Models Used:-
The different models that i have used are as follows:-

* Deepface

* CNN (Convolutional neural network)

* Xception

# DeepFace:-

DeepFace is a deep learning facial recognition system created by a research group at Facebook. It identifies human faces in digital images. The program employs a nine-layer neural network with over 120 million connection weights and was trained on four million images uploaded by Facebook users.The Facebook Research team has stated that the DeepFace method reaches an accuracy of 97.35% ± 0.25% on Labeled Faces in the Wild (LFW) data set where human beings have 97.53%. This means that DeepFace is sometimes more successful than the human being.

# Xception

Xception architecture is a linear stack of depth wise separable convolution layers with residual connections. This makes the architecture very easy to define and modify; it takes only 30 to 40 lines of code using a high level library such as Keras or Tensorflow not unlike an architecture such as VGG-16, but rather un- like architectures such as Inception V2 or V3 which are far more complex to define. An open-source implementation of Xception using Keras and Tensorflow is provided as part of the Keras Applications module2, under the MIT license. We used Adam as our optimizer after training for 70 epochs using Adam and a batch size of 785, we achieved 64% accuracy on the test set.

![xcept](https://user-images.githubusercontent.com/78207836/171469703-6f65c327-e41b-410d-99e9-824e373893f6.png)

The above image shows the final infrastructure of the Xception model. A fully connected neural layer that contains residual depth wise separable convolution where each convolution followed by batch normalization and Relu activation function. The last layer applies a global average pooling and softmax activation function to produce prediction.

# Using Transfer Learning Resnet 50:-

Since the FER2013 dataset is quite small and unbalanced, we found that utilizing transfer learning significantly boosted the accuracy of our model. ResNet50 is the first pre-trained model we explored. ResNet50 is a deep residual network with 50 layers. It is defined in Keras with 175 layers. We replaced the original output layer with one FC layer of size 1000 and a softmax output layer of 7 emotion classes. We used Adam as our optimizer after training for 50 epochs using Adam and a batch size of 785, we achieved 63.11% accuracy on the test set and 67% on the train set. There is much less over-fitting. We have taken epochs as 50. Once the threshold is achieved by the model and we further tried to train our model, then it provided unexpected results and its accuracy also decreased. After that, increasing the epoch would also not help. Hence, epochs play a very important role in deciding the accuracy of the model, and its value can be decided through trial and error.

# Custom Deep CNN:-

A Convolutional Neural Network (ConvNet/CNN) is a Deep Learning algorithm which can take in an input image, assign importance (learnable weights and biases) to various aspects/objects in the image and be able to differentiate one from the other.

We designed the CNN through which we passed our features to train the model and eventually test it using the test features. To construct CNN we have used a combination of several different functions such as sequential, Conv (2D), Batch Normalization, Maxpooling2D, Relu activation function, Dropout, Dense and finally softmax function.

We used Adam as our optimizer after training for 70 epochs using Adam with minimum learning rate 0.00001 and a batch size of 785, we achieved 69 % accuracy on the test set and 74% as train accuracy.

One drawback of the system is the some Disgust faces are showing Neutral .Because less no. of disgust faces are given to train .This may be the reason. I thought it was a good score should improve the score.

Thus, I decided that I will deploy the model.


![Rest](https://user-images.githubusercontent.com/78207836/171470084-d25dd4f2-d6d6-4d43-9a2e-870f26e27c74.png)

RESULTS / DISCUSSION Accuracy-Driven Models Table 1 shows the accuracies our best models achieved on the FER2013 private test dataset.

![m1](https://user-images.githubusercontent.com/78207836/171470449-0bf8571f-a4c4-4ec2-b449-fd019263eada.png)
![m2](https://user-images.githubusercontent.com/78207836/171470483-d1c3c265-90e4-49a9-84fd-3359e7be8294.png)

Most of the publications which achieved state-of-the-art accuracies on FER2013 utilized auxiliary training data. Table 1 demonstrates our accuracy gains from employing auxiliary data with care taken to avoid dataset bias. It also depicts our success in implementing class weighting, which significantly increased accuracies on frequently misclassified emotions. Table 2 demonstrates the weighted average of precision, Recall, F1 score parameters of the confusion matrix. From the table we can conclude that the best F1 score was obtained by CNN model.

![l1](https://user-images.githubusercontent.com/78207836/171470645-c33d7296-bc0b-4cfe-9d6e-d6d99ccf19c6.png)
![l2](https://user-images.githubusercontent.com/78207836/171470680-a6feb076-42dd-41f9-8554-3f3f4b304583.png)

=========================================================================================================

# Web APP
Rather than take a purely theoretical approach, we thought it would be challenging and novel to apply our work to the real world by developing a web app to run our model on-device in real-time. We deployed the app in Heroku. If you see in the starting section of GitHub repo you see that all the requirement files are there for creating an app on Heroku of name “face-emotion-recognition-off”. But due to high slug size the buffering takes time so we have run our app working on local and it ran properly and app is also fine also we’ve included video on GitHub repo.
HerokuLink: - https://face-emotion-recognition-akram.herokuapp.com/

==========================================================================================================

CONCLUSION
● We used different models but the Custom CNN model works pretty fine because it gives good accuracy result on test dataset.

● We build the WebApp using Streamlit and deployed in Heroku.

● The model which was created by custom CNN model gave training accuracy of 71% and test accuracy of 68%.

● I have also included the video of my WebApp working in Local.

