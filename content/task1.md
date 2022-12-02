---
title: "Task 1: Match-mismatch"
description: "given and EEG segment and two stimuli, classify which one of the input segments corresponds to the EEG"
menu: main
weight: 80
---
{{< figure src="../images/task_matchmismatch.png" title="Schematic overview of the match-mismatch task " >}}

# Description

Task 1 is a classification problem in a match-mismatch paradigm. In this paradigm, three inputs are presented to the model: 
1) a segment of EEG, 
2) the time-aligned speech stimulus (match)
3) an imposter stimulus (mismatch) 

The task of the model is to determine which of the input stimulus segments corresponds to the EEG. The performance metric is the classification accuracy (%). 

The input length of all (EEG, envelope) pairs is 3s. We define the mismatched stimulus to be temporally close to the matched one
by taking the segment starting either one second after the end of the matched segment or 4 seconds before the start of the matched segment.
Figure 2 contains an overview of the provided code and our recommended starting flow. We provide code to generate an envelope and
mel spectrogram representation from the raw audio files. However, participants can freely perform audio processing and use their preferred
representations.

In order to use the data in the classification paradigm, we implement and suggest the following methods. First, we present each EEG
segment twice to the model: (EEG, matched stimulus, mismatched stimulus, output label 0) and (EEG, mismatched stimulus, matched
stimulus, output label 1). Second, we make sure that a mismatched stimulus segment is also a matched segment with another EEG segment.
A way to do this is to ensure that the shift when windowing (1s in our code) is dividable by the spacing between the matched and mismatched
segment (1s). Failing to follow these suggestions is likely to result in models simply remembering the training samples and thus failing to
generalize to the test set.

The code for this task can be found on our [github repository](https://github.com/exporl/auditory-eeg-challenge-2023-code)

# Baseline

We include a [dilated convolutional network](https://ieeexplore.ieee.org/abstract/document/9287417?casa_token=t5BXK65duSYAAAAA:10B8PKULBXtxlxTZ6C_w1KoBIsELHfnkj4-QQ8EogEitMLnYKJmXcmZUabLF1AwyiO-qU3f-KKuc )  as a baseline for task 1. The dilated convolutional network consists of four steps. First, the
EEG channels are combined, from 64 to 8, using a 1D convolutional layer with a kernel size of 1 and a filter size of 8. Second, there are
N dilated convolutional layers with a kernel size of K and 16 filters. These N convolutional layers are applied to both EEG and envelope
stimulus segments. After each convolutional layer, a rectified linear unit (ReLU) is applied. Both stimulus envelope segments share the
weights for the convolutional layers. After these non-linear transformations, the EEG is compared to both stimulus envelopes, using cosine
similarity. Finally, the similarity scores are fed to a single neuron, with sigmoid non-linearity, to create a prediction of the matching stimulus
segment. When applied to the training and test sets of the challenge, a performance of approximately 77% correct is obtained.

 
# Evaluation criteria

The test set for the match-mismatch task contains half the data from test set 1 and half from test set 2. 

For test set 1, all test stimuli are
held-out stimuli. 

For test set 2, some stimuli have already appeared in the training set, but the subjects are unseen.


For these test sets, we will provide pairs of (EEG, stimulus 1, and stimulus 2), with a length of 3 seconds, each with a unique identifier
and a subject identifier. As an output, participants should submit a NumPy dictionary file to an online form on our website which contains the
predicted label for all EEG segments. Each entry in the submitted dictionary should be of the form **(EEG ID) : (label)**. In case of absent EEG
ID entries, the sample will be assigned the wrong label. Labels should be either 0 or 1.


For evaluation, we will calculate the mean accuracy score per subject. Then, we will calculate the mean over all the subjects means for both 
test set 1 and test set 2 and add them to obtain a final **score**, which will be updated in the online leaderboard. 


{{< figure src="../images/score_match_mismatch.jpg" title=" " >}}


