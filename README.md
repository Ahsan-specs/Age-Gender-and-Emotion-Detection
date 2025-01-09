Capstone Project by Ahsn Specs
Table of Contents
About
Technical System Architecture
Results
References
Installations
About
We created a prototype face recognition system based on three pre-trained CNN models that can identify faces and predict their gender, age, and emotions in an image or video.

The prototype is designed to be implemented in the retail industry for different applications:

Personalized Customer Experience
By linking the facial recognition system to a loyalty program, customer information and purchasing history could be displayed on the employee's smart devices. Based on this information, the salesperson could provide a premium, personalized experience to the customer, e.g. greet the customer by name and recommend their favorite products or new products suitable for their taste based on previous purchases.

Collect Customer Demographics
For unregistered customers, i.e. faces not registered in the system, the system can track their unique face vectors and gather useful demographic information, including gender and age estimations. Their purchase records can also be tracked by cameras at the checkout counter.

With this demographic data, the company can improve its customer segmentation and generate consumer-centered marketing strategies and more targeted in-store events.

Enhanced Store Traffic Analytics
The face recognition system can collect data about the number of shoppers that visit the store and their foot traffic patterns. It can also track the conversion rate, i.e., the percentage of shoppers who make a purchase. Furthermore, the system can identify hotspot areas where shoppers linger or areas with high foot traffic.

The benefits include analyzing foot traffic patterns to create more targeted and effective visual merchandising, identifying which in-store marketing promotions are most popular, and creating more accurate per-store revenue forecasts.

Tracking Customer Emotions
The face recognition system can also provide valuable feedback on in-store promotions by tracking customers’ emotional responses. This feedback helps retailers improve product assortment, visual merchandising, and tailor more effective promotional campaigns.

Improve Store Security
The face recognition system is valuable for preventing in-store crimes such as shoplifting. The store’s security team can be alerted if a person previously flagged for shoplifting enters the store, allowing them to be monitored more closely by security.

The significant savings from reduced in-store theft can then be passed on to customers in the form of lower product prices.

Technical System Architecture
Stages	Face Detection	Face Alignment	Face Feature <br> Extraction	Face Classification
ML Models			OpenFace.nn4
(Identity)
WideResNet
(Age, Gender)
mini_XCEPTION
(Emotions)	SVM Classifier
Libraries	Dlib	OpenCV	Keras
TensorFlow	Scikit Learn
Language	Python	Python	Python	Python
Results
[Left] System detected a new customer’s face at a promotion booth and shows the estimated gender, age, and emotion.
[Right] Video shows how a known customer is identified and how their emotion is being tracked.

We have trained the system on some celebrities and some of our friends, and we noted that in some cases, the two face vectors of two different people were even closer (in terms of Euclidean distance) than two photos of the same person. From our tests, using 5+ photos per person with clear, front-facing faces results in better identity estimates.

The SVM classifier is preferred over the KNN classifier, as it produces slightly better estimations. It also provides a confidence score for each estimate, which allows us to set a threshold to categorize known or new faces. We found that the best threshold was 0.3.

References
Face Detection: DLib
Face Alignment: OpenCV
Face Recognition Models:
OpenFace/ Facenet nn4.small model
Oarriaga/ mini_XCEPTION Emotion Model
WideResNet Age_Gender_Model
Face Recognition Explained and Codes: Karasserm
Age/Gender Prediction Explained and Codes: Chengwei
Installations
To run the model, please install the required Python packages using:

bash
Copy code
pip install -r requirements.txt
To run real-time demo:

bash
Copy code
python face_reco_demo.py
To run the face recognition model:

bash
Copy code
python face_reco_base.py
python face_reco_image.py
python face_reco_video.py
Image:

python
Copy code
face = FaceImage()
display_labeled_image(face, "sample/sample01.jpg")
Video to Video:

python
Copy code
labeled_video = FaceVideo("sample/sample02.mp4")
labeled_video.create_mp4_video("sample02vid.mp4")
Video to GIF:

python
Copy code
labeled_video = FaceVideo("sample/sample02.mp4")
labeled_video.create_animated_gif("sample02gif.gif")
To train new faces for face identification:
Import photos to faces/name_of_person/001.jpg and run the codes again.

To visualize face vectors of trained faces (using t-SNE dimension reduction):

python
Copy code
face_recognizer.visualize_dataset()
