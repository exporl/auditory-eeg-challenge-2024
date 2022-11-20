---
title: "Task 2: regression"
description: "Task 2: regression"
menu: main
weight: 80
---
{{< figure src="../images/task_regression.png" title="Schematic overview of the regression task" >}}

# Description 

Task 2 is a regression problem: To reconstruct the stimulus from the EEG. After reconstruction, a metric to measure the similarity is used
between the reconstructed stimulus and the original stimulus. In this task, we use the Pearson correlation. 

For this task, the stimulus representation is defined as the envelope, as described in the preprocessing section and as defined by the provided code. 
Participants are free to create their methods. However, remember that the stimulus
objective is fixed, as defined by the python file envelope.py.

The code for this task can be found on our [github repository](https://github.com/exporl/auditory-eeg-challenge-2023-code)



# Baseline {{< figure src="../images/code_flow_regression.png" title="provided code files and suggested starting point for the regresssion task" >}}

As a first baseline, we include a linear backward model. The linear model 
reconstructs the speech envelope from EEG by using a linear transformation across all 
channels and a certain time (the integration window). We use an integration window of 400ms.
We train subject-dependent models, i.e. there is one model per subject.  


As a second baseline, we include the [Very Large Augmented Auditory Inference (VLAAI) network](https://www.biorxiv.org/content/10.1101/2022.09.28.509945v2). The VLAAI network consists of
multiple (N) blocks, consisting of 3 different parts. The first part is a CNN stack, a convolutional neural network. This CNN consists of M=4
convolutional layers. The second part is a simple, fully connected layer of 64 units, which recombines the output filters of the CNN stack. The
last part is the output context layer. This special layers enhances the predictions made by the model up until that point, by taking the previous
context into account and combining it with the current sample. At the end of each block except the last, a skip connection is present with the
original EEG input. After the last block, the linear layer at the top of the VLAAI model combines the filters of the output context layer into a
single speech envelope. When applied to the training and test sets of the challenge, an average correlation score of 0.19 is obtained.



# Evaluation Criteria 
The test set for the regression task contains half the data from test set 1 and half from test set 2. All stimuli are held-out stimuli, i.e., they
do not appear in the training set. We have split up the stimuli into several smaller segments of 60 seconds and made these available with a
segment ID and a subject ID for each segment.

For each segment of 60 seconds, we expect a reconstructed envelope, which will then be compared to the original envelope, 
as calculated by the provided envelope script, using Pearson correlation. We will use the scipy.stats.pearsonr
 function to calculate the correlation value for each segment.

Afterwards, the mean correlation value per subject is calculated. Then, we calculate the mean correlation values over all subjects for test set 1 and test set 
2 and add both scores to obtain a final score, which will serve as the final ranking value.


Participants should submit a NumPy dictionary file for the test set to an online form on our website, which contains the reconstructed
envelopes for all EEG segments. Afterward, we will calculate the score mentioned above and update this in the online leaderboard. Each
entry in the submitted dictionary should be of the form (EEG ID) : (Reconstructed Envelope).
 
A correlation value of 0 will be taken in case of
absent EEG ID entries. The reconstructed envelope should be of dimensions 1 x 3840 (i.e., 60 seconds of data at the prescribed sample rate
of 64 Hz).

{{< figure src="../images/score_regression.png" title="Final score calculation" >}}