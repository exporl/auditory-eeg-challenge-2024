---
title: "Task 2: Regression"
description: "Reconstruct the stimulus from the EEG"
menu: task2
weight: 80
---
{{< figure src="../../images/task_regression.png" title="Schematic overview of the regression task" >}}

# Description 

Task 2 is a regression problem: To reconstruct the stimulus from the EEG. After reconstruction, a metric to measure the similarity is used
between the reconstructed stimulus and the original stimulus. In this task, we use the Pearson correlation. 

For this task, the stimulus representation is defined as the mel spectrogram, as described in the preprocessing section and as defined by the provided code. 
Participants are free to create their methods. However, remember that the stimulus
objective is fixed, as defined by the python file mel.py.

The code for this task can be found on our [github repository](https://github.com/exporl/auditory-eeg-challenge-2024-code)

# Baseline 

As a first baseline, we include a linear backward model. The linear model 
reconstructs the mel spectrogram from EEG by using a linear transformation across all 
channels and a certain time (the integration window). We use an integration window of 400ms.
We train subject-dependent models, i.e. there is one model per subject.  




# Evaluation Criteria 
The test set for the regression task contains half the data from the test set. All stimuli are held-out stimuli, i.e., they
do not appear in the training set. We have split up the stimuli into several smaller segments of 60 seconds and made these available with a
segment ID and a subject ID for each segment.

For each segment of 60 seconds, we expect a reconstructed mel spectrogram, which will then be compared to the original mel spectrogram, 
as calculated by the provided mel script, using Pearson correlation. We will use the scipy.stats.pearsonr
 function to calculate the correlation value for each segment and average the correlation across bands.

Afterwards, the mean correlation value per subject is calculated. Then, we calculate the mean correlation values over all subjects to obtain a final score, which will serve as the final ranking value.


Participants should submit a json dictionary file for the test set to an online form on our website, which contains the reconstructed
mel spectrograms for all EEG segments. Afterward, we will calculate the score mentioned above and update this in the online leaderboard. Each
entry in the submitted dictionary should be of the form (EEG ID) : (Reconstructed Mel).
 
A correlation value of 0 will be taken in case of
absent EEG ID entries. The reconstructed envelope should be of dimensions 10 x 3840 (i.e., 60 seconds of data at the prescribed sample rate
of 64 Hz).

{{< figure src="../../images/score_regression.png" title=" " >}}
