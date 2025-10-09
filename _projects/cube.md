---
layout: page
title: cube
description: The hallmark of colour in EEG signal
img: assets/img/publication_preview/cube.png
importance: 1
category: neuroimaging
toc:
  sidebar: left
---


# Abstract

Our perception of the world is inherently colourful, and colour provides well-documented benefits 
for vision: it helps us see things quicker and remember them better. We hypothesised that colour is 
not only central to perception but also a rich and decodable source of information in 
electroencephalography (EEG) signal recorded non-invasively from the scalp. Previous work has shown 
that brain activity carries colour information for uniform patches, but it remains unclear whether 
this extends to natural, complex images where colour is not explicitly cued. 
To investigate this, we analysed the THINGS EEG dataset, comprising 64-channel recordings from 
participants viewing 1,800 distinct objects (16,740 images) for 100 ms each, totalling over 
82,000 trials. We established a perceptual colour ground truth through a psychophysical 
experiment in which participants viewed each image for 100~ms and selected perceived colours 
from a 13-option palette. An artificial neural network trained to predict these scene-level colour 
distributions directly from EEG signals showed that colour information was robustly decodable 
(average F-score of 0.5).
We next modelled the interaction between colour and object perception in neuroimaging decoding. 
Images were segmented using the Segment Anything Model (SAM), each object was assigned a 
representative colour, and features were extracted from these colour-augmented images using CLIP 
vision encoders. We trained an EEG encoder, **CUBE** (**C**olo**U**r and o**B**j**E**ct decoding), 
to align features in both object and colour spaces. Across EEG and MEG datasets in a 
200-class recognition task, incorporating colour improved decoding accuracy by about 5%. 
Together, these findings demonstrate that EEG signal recorded during natural vision carries 
substantial colour information that interacts with object perception. Modelling this mutual 
interaction enhances neural decoding performance.

<p align="center">
<a href="https://github.com/ArashAkbarinia/CUBE"><img src="https://github.com/ArashAkbarinia/arashakbarinia.github.io/blob/master/assets/img/github_icon.png?raw=true" alt="Source Code" style="height:100px;"></a>
<a href="https://www.biorxiv.org/content/10.1101/2025.10.06.680651"><img src="https://github.com/ArashAkbarinia/arashakbarinia.github.io/blob/master/assets/img/publication_icon.png?raw=true" alt="Article" style="height:100px;"></a>
</p>