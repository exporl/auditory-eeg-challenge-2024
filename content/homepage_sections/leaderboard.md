---
title: "Get started"
weight: 40
description: "Get started"
---
## Get started

1) Send a mail to [auditoryeegchallenge@kuleuven.be](auditoryeegchallenge@kuleuven.be) with the names of the team members, emails, and affiliations. You will receive a password to download the data  
2) Download the data from [ICASSP-2023-eeg-decoding-challenge-dataset](https://homes.esat.kuleuven.be/~lbollens)
   - **split_data(.zip)** contains already preprocessed, split and normalized data; ready for model training/evaluation. If you want to get started quickly, you can opt to only download this folder/zipfile.
   - **preprocessed_eeg(.zip)** and **preprocessed_stimuli(.zip)** contain preprocessed EEG and stimuli files ( speech envelope and mel spectrogram features) respectively. At this stage data is not yet split into different sets and not normalized. To go from this to the data in **split_data.zip**, you will have to run _preprocessing_code/split_and_normalize.py_ .
   - **sub(_x.zip)** and **stimuli(.zip)** contain the raw EEG and stimuli files. If you want to process the stimuli and EEG files, you can run _preprocessing_code/sparrKULee.py_. This will start from the raw files, which are stored in the BIDS-format, and perform some commonly used preprocessing steps. You are free to adapt this code to your own needs.  Speech Envelope and/or mel spectrogram features will be stored in the processed_stimuli, eeg files in the preprocessed_eeg folder.  
   

For more details concerning the dataset, we refer to [the dataset paper](https://www.biorxiv.org/content/10.1101/2023.07.24.550310v1). 

3) Clone the starting code from our [github repository](https://github.com/exporl/auditory-eeg-challenge-2024-code) and get started. 
The repository contains preprocessing code, as well as baseline models for each of the tasks. Do ensure that you download the 2024 version of the data and the code, as both differ slightly from the challenge from last year. 
