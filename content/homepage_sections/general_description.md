---
title: "General description"
description: "General description"
---



## Challenge Call 


Various neuroimaging techniques can be used to investigate how the brain processes sound.
Electroencephalography (EEG) is popular because it is relatively easy to conduct and has a high temporal
resolution. Besides fundamental neuroscience research, EEG-based measures of auditory processing in the
brain are also helpful in detecting or diagnosing potential hearing loss. They enable differential diagnosis of
populations that can otherwise not be tested, such as young children or people with mental disabilities. In
addition, there is a growing field of research in which auditory attention is decoded from the brain, with
potential applications in smart hearing aids.
An increasingly popular method in these fields is to relate a person's electroencephalogram (EEG) to a
feature of the natural speech signal they were listening to. This is typically done using linear regression
to predict the EEG signal from the stimulus or to decode the stimulus from the EEG. Given the very low
signal-to-noise ratio of the EEG, this is a challenging problem, and several non-linear methods have been
proposed to improve upon the linear regression methods.
In the Auditory-EEG challenge, teams will compete to build the best model to relate speech to EEG. We
provide a large auditory EEG dataset containing data from 85 subjects who listen on average to 108 minutes
of single-speaker stimuli for a total of 157 hours of data. We define two tasks:

**Task 1 match-mismatch**: given two segments of speech and a segment of EEG, which segment of speech
matches the EEG?

**Task 2 regression**: reconstruct the speech envelope from the EEG.
We provide the dataset, code for preprocessing the EEG and for creating commonly used stimulus
representations, and two baseline methods.  

Teams can register by sending a mail to
auditoryeegchallenge@kuleuven.be with the names of the team members, emails, and affiliations.
