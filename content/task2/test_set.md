---
title: "Test Set Task 2"
description: "description of the test set for task 2"
menu: task2
weight: 80
---

---

### Provided test dataset

The test data for this task can be downloaded from [here](https://homes.esat.kuleuven.be/~lbollens/sparrkulee/test_set). 
The password is the same one as provided for the training set. 
The directory contains following items:
1) **sub-x_mapping.json**: These files link the EEG files to the possible stimuli. 
Since you are free to use whatever version of the data you want, these json files contain 
keys to the EEG files. Each entry in the json file is of the form:
**(segment_ID) : {'eeg': eeg_id}**.

2) **EEG data**: the EEG data is provided in three formats: preprocessed, raw and half-preprocessed. 
Each directory contains 20 subjects' test data in the format 
of sub-*.npz. Each  file contains a python dictionary with entries of the form: 
**eeg_id : EEG_data**. We provide the following three formats:
   - **preprocessed_eeg/sub-*.npz : Preprocessed EEG test samples**:
   If you used the already preprocessed data for training your models, this is the test data you want to use.
   The same preprocessing steps were applied to this data as to the training data and you can directly use it for testing. 
   Each EEG segment is 30 seconds long, sampled at 64 Hz and it contains 64 channels.
   - **raw_eeg/sub-*.npz : Raw EEG test samples**: 
   If you prefer to preprocess the EEG data yourself, you can use this directory. The EEG entries in this directory 
   are synchronized to the stimulus data, but other than that, no preprocessing was applied. All EEG entries are 5 seconds long,
   sampled at 1024~Hz. If you are interested in using these data, you can take a look at the [sparKULee_loadRAWtestfiles.py](https://github.com/exporl/auditory-eeg-challenge-2024-code/blob/main/preprocessing_code/sparKULee_loadRAWtestfiles.py) file. 
   This file loads in the raw EEG data and applies our preprocessing steps to it, in order to arrive at the preprocessed EEG data. 
   - **MWFilter_eeg/sub-*.npz : Half-preprocessed EEG test samples**:
   If you want to preprocess the EEG data yourself, but you want to use some of the same preprocessing steps as we did, you can use this directory.
   If you are interested in using these data, you can take a look at the [sparKULee_loadmwffiles.py](https://github.com/exporl/auditory-eeg-challenge-2024-code/blob/main/preprocessing_code/sparKULee_loadmwffiles.py) file.
   In more detail, this is data on which some of the preprocessing steps of our pipeline have been applied: 
     - aligment with stimulus 
     - highpass-filtering (SosFiltFilt)
     - Artifact interpolation
     - Artifact removal (MWFilter)

     Thus, the data is stored at 1024 Hz, but the data is not yet downsampled to 64 Hz. 
     We opted to include these data, since some of the preprocessing steps, namely the artifact removal using a MWF filter, use an average over time to remove the artifacts.
     When using segments of just 5 seconds, these steps are not as effective as when using longer segments and might produce different results. For the 30 seconds windows of the regression task, we hypothesize that this pose less of a problem, however, you are still free to use these files.  
     If you have any more questions about these data, please contact us.

If you have any more questions about these data, or about the usage of raw data, please contact us.

### Usage example 
If you use the preprocessed version of the EEG data
you can use [the provided code](https://github.com/exporl/auditory-eeg-challenge-2024-code/blob/main/task2_regression/experiments/test_regression.py) to load in the data and use it for testing.
This code will load in a baseline pretrained model, 
loop over all the data of the test set, predict the reconstructed Mel and return json files in the correct format.





### Expected output 

 As an output, participants should upload a zip file, containing json files to [the following link](https://kuleuven-my.sharepoint.com/:f:/g/personal/lies_bollens_kuleuven_be/EhTPDzpHeg1LoLxmRNNt968BLSEFSJ8F6TecZepRHhdjMg)
 The files should follow the following naming convention: 
 
 task_2_group_**group_name**_submission _**submission_number**.zip
 
 where **submission_number** should be 1 for 
 the first submission and can go up to 2. We will use the latest submission as the final submission, from which the ranking will be calculated. Groups that have not yet supplied their group name, should send a mail to the
 organisers where they specify their name. When uploading, you will be prompted to enter a name. Please enter the name of one of the officially registered participants. 
 
The json file(s) should contain the predicted mel spectrograms for all ID segments, which can be found in the mapping ( in the form of **(segment_ID) : {'eeg': eeg_id}**.)
Each entry in the submitted file should be of the form **segment_ID : reconstructed Mel**.


A correlation value of 0 will be taken in case of absent EEG ID entries. 
The reconstructed mel should be of dimensions 10 x 1920 (i.e., 30 seconds of data at the prescribed sample rate of 64 Hz). 

For evaluation, we will calculate the mean correlation score over bands, per subject. Then, we will calculate the mean over all the subjects means to obtain a final **score**, which will be updated in the online leaderboard.
