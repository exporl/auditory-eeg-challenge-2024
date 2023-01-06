---
title: "Test Set Task 2"
description: "description of the test set for task 2"
menu: main
weight: 80
---

# task 2
 
### Expected Output 

 As an output, participants should upload a zip file, containing json files to [the following link](https://kuleuven-my.sharepoint.com/:f:/g/personal/lies_bollens_kuleuven_be/EhUxPLaiLjBInBAHEY3NNmYBVZMF8W-FtHojulxtY0k7RQ)
 The files should follow the following naming convention: 
 
 task_2_group_**group_name**_submission _**submission_number**.zip 
 
 where **submission_number** should be 1 for 
 the first submission and can go up to 5. We will use the latest submission as the final submission, from which the ranking will be calculated. Groups that have not yet supplied their group name, should send a mail to the
 organisers where they specify their name. When uploading, you will be prompted to enter a name. Please enter the name of one of the officially registered participants. 
 
 
The json file(s) should contain the predicted labels for all EEG segments.Each entry in the submitted dictionary should be of the form (EEG ID) : (Reconstructed Envelope).
 
A correlation value of 0 will be taken in case of absent EEG ID entries. The reconstructed envelope should be of dimensions 1 x 3840 (i.e., 60 seconds of data at the prescribed sample rate
of 64 Hz).
We provide the script [predict_test.py](), which loads a pretrained model, loops over all the data of the test set, predicts the output labels and returns json files
in the correct format. 

For evaluation, we will calculate the mean correlation score per subject. Then, we will calculate the mean over all the subjects means for both 
test set 1 and test set 2 and add them to obtain a final **score**, which will be updated in the online leaderboard. 
