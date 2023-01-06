---
title: "Test Set Task 1"
description: "description of the test set for task 1"
menu: main
weight: 80
---

---

### Provided test dataset

The test data for this task can be downloaded from [here](https://path).
The directory contains following items:
1) **Preprocessed EEG test samples**: The main directory contains 84 subjects' test data in the format 
of subject_name.json. Note that there is no test data for sub-001. Each json file contains a python dictionary with 
sample IDs as keys and tuples in the format of (EEG, speech1, speech2) as values. First element of the tuple is preprocessed
EEG of 3 seconds long with fs=64 Hz. speech1 and speech2 are pointers to the actual speech segments which are located 
in the envelope_segments and/or stimuli_segments. You need to probably convert EEG from list to numpy array.

2) **envelope_segments**: This directory contains envelope of speech segments used in the test samples. You can already use this 
directory if you trained your model with envelope as speech feature. You can get the Envelope by using the following code:

    *import numpy as np*
    
    *data = np.load(speech_seg.npz)*
    
    *speech, fs = data['envelope'], data['fs']*

3) **raw_eeg**: We also provide the corresponding raw EEG files for each subject. If you prefer to have access
to the raw EEG and do your own preprocessing, then you can use this directory. The json files in this directory have exactly
the same format as of the preprocessed EEG files. Sampling rate of the raw EEG is 1024 Hz.

4) **stimuli_segments**: This directory contains raw speech segments at 48 kHz. You can load the raw stimulus segments
using the following code:

*data = np.load(speech_seg.npz)*

*speech, fs = data['audio'], data['fs']*



### Expected output 

 As an output, participants should upload a zip file, containing json files to [the following link](https://kuleuven-my.sharepoint.com/:f:/g/personal/lies_bollens_kuleuven_be/EqTaLSL7EQ5EtDgSf-W844QBKuAbvuJoagzaVBZEtDx7Dw)
 The files should follow the following naming convention: 
 
 task_1_group_**group_name**_submission _**submission_number**.zip
 
 where **submission_number** should be 1 for 
 the first submission and can go up to 5. We will use the latest submission as the final submission, from which the ranking will be calculated. Groups that have not yet supplied their group name, should send a mail to the
 organisers where they specify their name. When uploading, you will be prompted to enter a name. Please enter the name of one of the officially registered participants. 
 
The json file(s) should contain the predicted labels for all EEG segments. Each entry in the submitted file should be of the form **(EEG ID) : (label)**. In case of absent EEG
ID entries, the sample will be assigned the wrong label. Labels should be either 0 or 1. 

We provide the script [predict_test.py](https://github.com/exporl/auditory-eeg-challenge-2023-code/blob/main/task1_match_mismatch/experiments/predict_test.py), which loads a pretrained model, loops over all the data of the test set, predicts the output labels and returns json files
in the correct format. 

For evaluation, we will calculate the mean accuracy score per subject. Then, we will calculate the mean over all the subjects means for both 
test set 1 and test set 2 and add them to obtain a final **score**, which will be updated in the online leaderboard. 
