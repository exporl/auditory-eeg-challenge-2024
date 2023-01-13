---
title: "Registration"
description: "Use the link below"
menu: main
weight: 80
---

# Registration
Teams can register by sending a mail to
auditoryeegchallenge@kuleuven.be with the names of the team members, emails, and affiliations. Upon confirmation, teams will receive access to the training data. 


# Guidelines for participants

- Participants can submit their predictions up to five times. The latest received submission counts as the official score.
- The Audio-EEG challenge features two separate tasks. Participants can submit to either one track or both. Results should be accom-
panied by a 2-page paper describing the proposed method
- The top 5 ranked teams will be invited to submit a 2-page paper, to be presented at ICASSP-2023, which should be submitted before
the camera-ready deadline. In addition, they will receive an invitation to submit a full paper about their work to the IEEE Open Journal
of Signal Processing (OJ-SP). Submitted OJ-SP papers will undergo peer review by the OJ-SP Editorial Board in collaboration with
the IEEE SPS CDC committee and ICASSP-2023 GC Chairs.
- Winners will be selected according to the best performance for every single task. One winner for each task will be selected
- The top 5 teams will be determined as follows: the top 2 teams for track 1 and the top two teams for track 2. The fifth team will be
chosen as the third-ranking team in the task with the most submissions.
- Each participant can only be included in one participating team    
- Participants can use the full training set to train the models for both tasks. We encourage the participants to explore different prepro-
cessing and data augmentation methods to better train the models. All stimulus information can be used for training, provided that the
information can be deduced based on the training set.
- All parameters should be tuned on the training set. The test sets can be used only in an evaluation paradigm to provide output
labels/predictions.
- Upon submission, we ask that the teams submit their code, along with the generated predictions. This code will not be shared and the intellectual property belongs to the participants at all times. 
- Additionally, we encourage all teams to publically share their code at the end of the contest. 
- The use of external data (both training data and/or pretrained models) is allowed, on the following conditions: 
    1. The datasets, or pretrained models, should be publicly and freely available. Participants wishing to use data/models that are publicly available, but not free, should contact the organisers to discuss if the data can be used. 
    2. Only datasets/pretrained models that have been made publicly available before the start of this challenge, i.e. **put online before November 21, 2022**, are allowed to be used. 
    3. Upon submission of their results, teams should explicitly mention which extra datasets/model weights they have used to generate their predictions.
    4. You can still use a publicly available pretrained model even if the data which the model is trained on is not open to public.
- Participants can fine-tune their model on each test subject to have a subject specific model (this can only be done for subjects that are also present in the train set).
