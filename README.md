# CP_EEG
Kanawut (Poon) st122109 \
Worachot (Ball) st122153 \
Chanakarn (Opal) st122409

---
**Sunday, 14 NOV 2021**

** Main Achievements**

- We have tried using deep neural network on the first partcipant, the performance accuracy is at around 70%, slightly better than SVM.
- We have created the class partcipantData that helps genenerate all the dataset from 16 participants and 3 sessions, with customizable frequency band.

** Next Step**
- Ball works on presentation slides: scope overview and project approach
- Opal works on presentation slides: project initiative
- Poon works on creating the class sessionData that that helps genenerate all the dataset from 16 participants and 3 sessions, with customizable frequency band
- Each of us tries to use theses clases to train and test with SVM and NN to find the best hyperparameters. The result will be stored in the google sheet table

---

**Sunday, 7 NOV 2021**

**Main Achievements**
- Taking the feedback from prof, we tentatively finalize the main hypothesis that our project tries to focus. These following are inspired by multiples papers related to SEED-V

      HYPOTHESIS & SCOPE
      1) Compare the performance of each 5 frequency bands (alpha, beta, gamma, theta, delta) on emotion recognition. (Any band is more important?)
      2) Classification recognition by training on individual-dependent approch VS session-dependent approach
      3) Normalization by using the pre-stimulated stages
      
      2 classification models: SVM and Deep Neural Network
      
CODING
      
- We have successfully extracted the events of each participant sessions.
- We found out that the dataset files from the SEED-V institute has already been cleaned and preprocessed into Differential Entropy through Fourier Transformation. So as to practice how to get there, we are using a raw format file to try preprocessing and extracting features into the same output. However, we are now struggling with applying Fourier Transformation on our dataset.
- We organized the pre-processed data into X, y and tried our first SVM classfication that yields accuracy of 67%, almost the same as our reference paper.

READING & OTHERS
 
- Opal has shared the new paper *"Review on Emotion Recognition Based on Electroencephalography"*. This one provides broad end-to-end overview of how to preprocess, extract features and train EEG related to emotion recognition
- Poon has shared the new paper *"Classification of 5 Emotions of EEG and Eye Movement Signal: Discrimination Ability and Stability over Time"*. This papers works on SEED-V by using brain signal, eye movement and the combined modalities to predict the sentiment recognition
- Ball has shared some of the github repo that works on MNE coding library


**NEXT STEPS**
- each of us will read the additional, abovementioned papers from Opal and Poon. As it will be used as main referened papers.
- each of us will try working on Fourier transformation, and try implementing differernt models according to our hypothesis.


---
**Sunday, 31 OCT 2021**

**Main Achievements**
- We have finished the basic data proprocessing. Luckily, in our dataset, the powerline noise has been removed. 
- So we go to next steps: bandpass filtering and implemented ICA to remove some of the insignificant channels /features (5 removed from 16 ICAs)
- We are creating the y label which represents the audience sentiment for each movie clip in each session


**CHALLENGE & LESSON**
- We tried to follow professor's instruction code, but it was originally in csv. We tried to replicate our cnt.file to csv, but turned out that the opearations took so much time, and resulted in error
- For some reason, our dataset, when assinged to set_montage, keeps returning error that there are no EEG channels. That prevents us from furthering to the next process. At first, we tried using parameter 'on_missing = 'ignore'' to avoid the errors, but ended up seeing more errors during the ICA process.
- We digged deep to MNE documentation to find out what solutions can be done. We even created our own montage, but still failed to make it run.
- Lastly, we ended up removing channels that caused the error. We also tried parameter match_case = False, to allow some different EEG names
- After all the preprocessing, in our dataset, the y label is not available, making us still stuck with creating it for training-the-model part. We saw 2 different approaches. One using Epoch like professor's code, and the other from paper creating each matrix for each movie clip session and then stacking together.

**Next Steps**
- Finish X,y and start training at least one model
- After getting the first result, try some different data preprocessing and implementation to compare model accuracy.


---
**Sunday, 24 OCT 2021**

**Article**
- Each of us presented at least 1 artciles related to EEG emotion analysis
- Opal presented (1) *Comparing Recognition Performance andRobustness of Multimodal Deep Learning Models for Multimodal Emotion Recognition  and (2)Classification of Five Emotions from EEG and Eye Movement Signals: Complementary Representation Properties*
- Poon presented *Leveraging spatial-temporal convolutional features for EEG-based emotion recognition*
- Ball presented *EEG Emotion Classification Using an Improved SincNet-Based Deep Learning Model*
- All the presentation slides of summary and key points to integrate into our project is https://1drv.ms/p/s!Am04WExKvjhatlWCU9wQJqCX460i?e=ci1OSl 


**Coding**
- We decided to create new gmail account to used shared Google Drive to run Google Colab https://colab.research.google.com/drive/1fCFv7vVP3fxOnBOqEujyMNy38dHH77-v?usp=sharing
- We started reading the first file (as large as almost 1GB!) and explored the data to understand its shape, features 

**Challenge & Questions!!!**
- We spent a couple of hours finding way to read the .cnt file.
- We have questions such as how many files or participants we need to use for our training model. We have as many as 48 files (each file is from each particpant's brain) but each is very large (almost 1GB per file)
- We are not sure whether we need to read all files and concatenate all the files first and then train the model, or we can use only 1 file to train the model then use that model to retrain on the next file.
- The label y is provided in label encoded format (0,1,2,3,4) for 5 different emotion classes, but we are thinking whether we need to use the one-hot encoder instead so that we can use the cross-entropy loss function on the predicted probability of each class

**Next Steps**

Basically, we are aiming at train and test the first NN model on this first file
- So, we need to transform the provided y label to one-hot encoded format
- Data preprocessing such as: bandpass limit, power line dropping, artefact removal, Fourier transformation, ICA
- Create the first NN model to train, predict and test the result


---
**Sunday, 17 OCT 2021**
- Opal already acquired the SEED-V dataset from BMCI and uploaded all the datasets into https://drive.google.com/drive/folders/1LvlpX7BbJ321JfBjQs50vvq53-RBEk3W?usp=sharing
- Poon read and talked briefly about "EEG-Based BCI Emotion Recognition: A Survey" that tries to explore multiple methodologies that can be utilized from signal acquistion > preprocession > feature extraction > analysis > performance evaluation
- Ball suggested creating the visual Gantt Chart to keep track of the project progress; https://1drv.ms/x/s!Am04WExKvjhatjisHgtbeXgzAhhi?e=0GYhE7
- Article allocation (each select 2 article, and all articles will uploaded into the "RelatedArticle" folder

POON \
      - Leveraging spatial-temporal convolutional features for EEG-based emotion recognition https://github.com/CarlOsito16/CP_EEG/blob/main/RelatedArticle/Leveraging%20spatial-temporal%20convolutional%20features%20for%20EEG-based%20emotion%20recognition.pdf \
      - Technological advancements and opportunities in Neuromarketing:a systematic review https://github.com/CarlOsito16/CP_EEG/blob/main/RelatedArticle/Neuromarketing.pdf
      
BALL \
      - EEG Emotion Classification Using an Improved SincNet-Based Deep Learning Model https://github.com/CarlOsito16/CP_EEG/blob/main/RelatedArticle/brainsci-09-00326-v2.pdf \
      - An Investigation of Deep Learning Models for EEG-Based Emotion Recognition https://github.com/CarlOsito16/CP_EEG/blob/main/RelatedArticle/fnins-14-622759.pdf 
      
OPAL \
      - Comparing Recognition Performance andRobustness of Multimodal Deep Learning Models for Multimodal Emotion Recognition https://github.com/CarlOsito16/CP_EEG/blob/main/RelatedArticle/Comparing%20Recognition-2021.pdf \
      - Classification of Five Emotions from EEG and Eye Movement Signals: Complementary Representation Properties https://github.com/CarlOsito16/CP_EEG/blob/main/RelatedArticle/Compare%20five%20emotion_2019.pdf
      
- Reference to github analyzing the same dataset: https://github.com/csliuwei/MI_plot


Next step:  
- Poon finishes Gantt chart
- Each member reads and presents at least 1 selected article with 1-page presenation summary
- Each tries to start exploring the dataset and finalize the main work file

---

**Sunday, 10 OCT 2021**
- Each member searched and presented 2 datasets of their interest to the group
(Poon - Neuromarketing, Arousal for producitity, Ball - Motor sensoring and DEAP Emotion, Opal - Sleep-related EEG, Emotions classfication while watching movies(SEED5))
- After discussion, we agreed on selecting Opal's 'SEED5' that focuses on classifying emotions/ feeling of movies viewers into 5 categories (happy, sad, disgust, fear, neutral)
- To make things more interesting, we plan to integrate the neuromarketing side of whether or not the audience like or dislike the film
- Link to dataset: https://bcmi.sjtu.edu.cn/home/seed/index.html
- Link to article about the selected dataset: https://www.mdpi.com/1424-8220/20/18/5083#framed_div_cited_count

Next step:  
- Each of us will find 2 articles related to the selected topic 'SEED5' and will share the brief summary of each article
- Opal will contact the linked site to request data for further work
