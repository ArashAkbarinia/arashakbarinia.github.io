---
layout: page
title: cube
description: The hallmark of colour in EEG signal
img: assets/img/cube.png
importance: 1
category: neuroimaging
toc:
  sidebar: left
---


# Abstract

Our perception of the world is inherently colourful, and colour has well-documented benefits for 
vision: it helps us recognise objects faster and remember them better. We hypothesised that colour 
is not only central to perception but also a rich and decodable source of information in 
electroencephalography (EEG) signal recorded non-invasively from the scalp. Previous studies have 
shown that brain activity carries colour information when participants viewed single patches of 
uniform colour. However, it remains unclear whether this extends to natural, complex images where 
colour is not explicitly cued. 
To investigate this, we analysed the THINGS-EEG dataset, which comprises 64-channel EEG recordings 
from participants viewing 1,800 distinct objects (16,740 images) for 100 ms each in a rapid serial 
visual presentation paradigm, totalling over 82,000 trials. We established a perceptual colour 
ground truth through an online psychophysical experiment, in which participants viewed each image 
for 100 ms and selected all perceived colours from a 13-option palette. We then trained an 
artificial neural network to predict these scene-level colour distributions directly from 
EEG signal, and found that colour information was robustly decodable (average F-score about 0.5).
We next examined whether colour could enhance EEG-based object decoding. Given the strong link 
between colour and object perception, we segmented images using the Segment Anything Model (SAM), 
assigned each object a representative colour based on its average pixel values, and 
extracted features from these colour-augmented images using CLIP vision encoders. We trained an 
EEG encoder---**CUBE** (**C**olo**U**r and o**B**j**E**ct decoding)---to align features not only 
in object space but also in colour space. Across both the THINGS EEG and MEG datasets in a 
200-class object recognition task, our results show that incorporating colour features improves 
decoding accuracy by about 5% in both individual and group analyses, consistently across seven 
tested vision encoders.
Together, these findings demonstrate that EEG signal recorded during natural vision carries 
substantial colour information that interacts with object perception. Modelling this mutual 
interaction enhances neural decoding performance. This work establishes a novel approach to 
studying the neural representation of colour and its role in supporting visual cognition.