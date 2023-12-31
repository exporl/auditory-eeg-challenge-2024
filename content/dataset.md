---
title: "Dataset"
description: "The official dataset of the challenge"
menu: main
weight: 80
---


The training set can be downloaded here, using the password which will be provided to all registered teams: [ICASSP-2024-eeg-decoding-challenge-dataset](https://homes.esat.kuleuven.be/~lbollens)

For more details concerning the dataset, we refer to [our dataset paper](https://www.biorxiv.org/content/10.1101/2023.07.24.550310v1).
 


# EEG

Electroencephalography (EEG) is a non-invasive method to record electrical activity in the brain, which is generated by ionic currents that
flow within and across neuron cells. When a large population of thousands or millions of neurons with a similar orientation in a specific brain
region synchronises its electrical activity, the produced electrical field is large enough to be observable on the scalp. When we attach an array
of electrodes on the scalp, these electrical fields can be recorded by measuring the electrical potential (typically 10 − 100μV) between pairs
of electrodes in the array.


# Data Collection

We measure EEG data in a well-controlled lab environment (soundproof and electromagnetically shielded booth), using a high-quality 64-
channel Biosemi ActiveTwo EEG recording system with 64 active Ag-AgCl electrodes and two extra electrodes, which serve as the common
electrode (CMS) and current return path (DRL). The data is measured at a sampling rate of 8192 Hz. While the temporal resolution is high,
the spatial resolution is low, with only 64 electrodes for billions of neurons. All 64 electrodes are placed according to international 10-20
standards.

The dataset contains data from 105 young, normal-hearing subjects (all hearing thresholds <= 25 dB Hl), with Dutch as their native
language. Subjects indicating any neurological or hearing-related medical history were excluded from the study. The study was approved by
the Medical Ethics Committee UZ KU Leuven/Research (KU Leuven, Belgium). All identifiable subject information has been removed from the dataset. 

Each subject listened to between 8 and 10 trials, each of approximately 15 minutes in length. The order of the trials is randomized
between participants. All the stimuli are single-speaker stories spoken in Flemish (Belgian Dutch) by a native Flemish speaker. We vary the
stimuli between subjects to have a wide range of unique speech material. The stimuli are either podcast or audiobooks. Some audiobooks are
longer than 15 minutes. In this case, they are split into two trials presented consecutively to the subject.


{{< figure src="../images/train_test_division.png" title="Division into train and test set" >}}




The dataset contains data from 105 young, normal-hearing subjects (all hearing thresholds <= 25 dB Hl), with Dutch as their native language. Subjects indicating any neurological or hearing-related medical history were excluded from the study. The study was approved by the Medical Ethics Committee UZ KU Leuven/Research (KU Leuven, Belgium). All identifiable subject information has been removed from the dataset.

Each subject listened to between 8 and 10 trials, each of approximately 15 minutes in length. The order of the trials is randomized between participants. All the stimuli are single-speaker stories spoken in Flemish (Belgian Dutch) by a native Flemish speaker. We vary the stimuli between subjects ( between each 2 to 26 subjects) to have a wide range of unique speech material. The stimuli are either podcast or audiobooks. Some audiobooks are longer than 15 minutes. In this case, they are split into two trials presented consecutively to the subject.

## Training set
The training set contains data from 85 subjects and is equal to the training + test set from the ICASSP 2023 Auditory EEG competition. In total, the training set contains 655 trials( of 15 minutes each) , from 85 subjects, using 72 different stimuli, for a total of 9420 minutes ( 157 hours).

## Test set
The test set contains data from 20 subjects, which have been newly measured for the ICASSP 2024 auditory EEG competition. All subjects, as well as the stimuli, are never seen in the training set. The test set contains a total of 20 subjects, 15 different stimuli, for a total of 2315 minutes of data ( 38 hours).
The test sets will be released to the public on November 15,2023.

We provide two different versions of the dataset. The first data version is the raw EEG data, which has been downsampled from 8192 Hz to 1024 Hz and is stored in the BIDS format. The second version of the data has been preprocessed ( we provide code to replicate these steps) First, the artefacts are removed, using a multichannel Wiener filter. Then, the EEG signal is re-referenced to a common average and finally, the EEG signal is downsampled to 64 Hz. These steps are commonly used in EEG signal processing, and the preprocessed version can be used directly in machine learning models. However, challenge participants are free to perform their own preprocessing on both versions of the datasets.

# Ethics   
Before commencing the EEG experiments, all participants read and signed an informed consent form approved by the
Medical Ethics Committee UZ KU Leuven/Research (KU Leuven, Belgium). All participants in this dataset gave 
explicit consent for their pseudoanonymized data to be shared in a publicly accescible dataset. 
All identifiable subject information has been removed from the dataset. 