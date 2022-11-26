---
title: "Get started"
description: "Get started"
---
## Get started

1) Send a mail to [auditoryeegchallenge@kuleuven.be](auditoryeegchallenge@kuleuven.be) with the names of the team members, emails, and affiliations. You will receive a password to download the data  
2) Download the data from [ICASSP-2023-eeg-decoding-challenge-dataset](https://kuleuven-my.sharepoint.com/:f:/g/personal/lies_bollens_kuleuven_be/EkaIjOmoPIRHmYLdLK8b2VQBY_2ouqNSnHHTHyRl3Zn-2w?e=KhX7d0)
   - **split_data(.zip)** contains already preprocessed, split and normalized data; ready for model training/evaluation. If you want to get started quickly, you can opt to only download this folder/zipfile.
   - **preprocessed_eeg(.zip)** and **preprocessed_stimuli(.zip)** contain preprocessed EEG and stimuli files (envelope and mel features) respectively. At this stage data is not yet split into different sets and normalized. To go from this to the data in split_data, you will have to run run_splitting_and_normalization.py.
   - **raw_eeg(_x.zip)** and **stimuli(.zip)** contain the raw EEG and stimuli files. If you want to process the stimuli files, you can run run_preprocessing.py. The processed stimuli files will be stored in the processed_stimuli. Currently, no preprocessing code is made available to preprocess EEG, so you will have to write your own implementation or use the precomputed processed_eeg folder.


3) Clone the starting code from our [github repository](https://github.com/exporl/auditory-eeg-challenge-2023-code) and get started. 
The repository contains preprocessing code, as well as baseline models for each of the tasks. 