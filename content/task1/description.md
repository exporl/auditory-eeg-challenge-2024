---
title: "Task 1: Match-mismatch"
description: "given an EEG segment and X stimulus segments, classify which one of them corresponds to the EEG"
menu: task1
weight: 80
---
{{< figure src="../../images/task_matchmismatch.png" title="Schematic overview of the match-mismatch task " >}}

# Description

Task 1 is a classification problem in a match-mismatch paradigm. Last year (ICASSP 2023 edition), the challenge was to select the matched stimulus
segment among two candidates. This year, we modify the paradigm to make it more challenging, by presenting  five candidates to the model.  
The complete input to the model is structured as follows:

1) a segment of EEG, 
2) the time-aligned speech stimulus (matched segment)
3) four imposter stimuli (mismatched segments) 

The task of the model is to determine which of the input stimulus segments corresponds to the EEG. The performance metric is the classification accuracy (%).

The segment length of all (EEG, envelope) pairs is either 5s. We define the mismatched stimuli to be selected arbitrarily among windows from the same story after the signal was chunked.
Figure 2 contains an overview of the provided code and our recommended starting flow. We provide code to generate an envelope and
mel spectrogram representation from the raw audio files. However, participants can freely perform audio processing and use their preferred
representations.

In order to use the data in the classification paradigm, we implement and suggest the following methods. First, we present each EEG
segment five times to the model: (EEG, matched stimulus, mismatched stimulus 1, mismatched stimulus 2, mismatched stimulus 3, mismatched stimulus 4), output label [1, 0, 0, 0, 0])
 ,(EEG, mismatched stimulus 4, matched stimulus, mismatched stimulus 1, mismatched stimulus 2, mismatched stimulus 3), output label [0, 1, 0, 0, 0])
 ..., 
 ,(EEG, mismatched stimulus 1, mismatched stimulus 2, mismatched stimulus 3, mismatched stimulus 4, matched stimulus), output label [0, 0, 0, 0, 1]) 
Second, we make sure that a mismatched stimuli segments are also a matched segment with another EEG segment.
A way to do this is to ensure that the shift when windowing is dividable by the spacing between the matched and mismatched
segment. Failing to follow these suggestions is likely to result in models simply remembering the training samples and thus failing to
generalize to the test set. Although mismatched segments are selected randomly, we advise to assign mismatched segments equally to different 
positions in the inputs to avoid the model learning spurious cues (i.e., label learning).

The code for this task can be found on our [github repository](https://github.com/exporl/auditory-eeg-challenge-2024-code)

# Baseline

We include a [dilated convolutional network](https://ieeexplore.ieee.org/abstract/document/9287417?casa_token=t5BXK65duSYAAAAA:10B8PKULBXtxlxTZ6C_w1KoBIsELHfnkj4-QQ8EogEitMLnYKJmXcmZUabLF1AwyiO-qU3f-KKuc) 
integrating  5 stimulus segments as baselines for task 1. Though there are now 5 stimulus segments, the model is easily adaptable to include more or less mismatched 
segments and we encourage participants to experiment with different numbers of mismatches and window lengths to see how this influences training, and accuracy. 
 
The dilated convolutional network consists of four steps. First, the
EEG channels are combined, from 64 to 8, using a 1D convolutional layer with a kernel size of 1 and a filter size of 8. Second, there are
N dilated convolutional layers with a kernel size of K and 16 filters. These N convolutional layers are applied to both EEG and envelope
stimulus segments. After each convolutional layer, a rectified linear unit (ReLU) is applied. All stimulus envelope segments share the
weights for the convolutional layers. After these non-linear transformations, the EEG is compared to each stimulus envelopes, using cosine
similarity. Finally, each obtained similarity matrices are fed to an individual neuron, with a linear activation function. The resulting outputs 
(corresponding to the number of stimulus segments) are fed into a non-trainable softmax layer which selects the matching segment. 
When applied to the training and test sets of the challenge for 3~s segments, a performance of approximately 62% and 48% correct is obtained when 
using two and four mismatched segments respectively.

 
# Evaluation criteria

The test set for the match-mismatch task contains data from 20 new, unseen subjects, listening to both podcasts and audiobooks. 
We provide inputs in the form:(EEG, stimulus 0, stimulus 1,  stimulus 2, stimulus 3 and stimulus 4) , with a length of 5 seconds, each with a unique identifier.
 As an output, participants should submit a json dictionary file to an online form on our website which contains the
predicted label for all EEG segments. Each entry in the submitted dictionary should be of the form **(EEG ID) : (label)**. The label is an integer, corresponding to which stimulus matches the EEG (eg. 0 if stimulus 0 matches the EEG, ... 4 if stimulus 4 matches the EEG). 
In case of absent EEG ID entries, the sample will be assigned a wrong label.


For evaluation, we will calculate the mean accuracy score per subject, per test case. Then, we will calculate the mean over all the subjects means and add them to obtain four final scores. , which will be updated in the online leaderboard. 




