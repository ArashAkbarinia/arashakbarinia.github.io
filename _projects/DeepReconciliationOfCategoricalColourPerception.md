---
layout: page
title: colourcats
description: Deep Reconciliation of Categorical Colour perception
img: assets/img/DeepReconciliationOfCategoricalColourPerception/logo.png
importance: 1
category: work
---


# Deep Reconciliation of Categorical Colour perception

We perceive colours categorically. Our perceptual system separates a continuous space into distinct 
categories. The most prominent example is the rainbow, there are no discontinuities in its colour
spectrum, yet we see discrete bands. The underlying reason, particularly the role of language, 
has spawned a heated debate between universalists and relativists. We reconcile these two 
explanations by studying vision-language and pure-vision deep neural networks (DNN). The results of 
our odd-one-out experiments show that pure-vision models 
(e.g., ImageNet object recognition networks) explain 85% of human data. In turn, suggesting 
a large part of our categorical colour perception is purely driven by visual signals. 
The remaining 15% is explained with vision-language models 
(e.g., CLIP text-image matching networks) even when tested without their language module. 
In turn, suggesting colour categories is a free-from-language representation, yet linguistic 
colour terms have influenced its development. We investigated whether colour categories emerge
in all pure-vision models by studying Taskonomy networks trained on 24 visual tasks. 
Human-like colour categories appear only in less than half of those models, namely, 
networks trained on semantic (e.g., image segmentation, object recognition, and 
scene classification) or 3D tasks (e.g., shade from shaping, surface normal prediction, 
and depth estimation). Our results show low-level tasks (e.g., autoencoding and denoising) 
never obtain human-like colour categories. It also matters whether a network is trained on 
2- or 3-dimensional outputs for the same perceptual task. Networks trained on 3D tasks of 
edge and keypoint detection obtain human-like colour categories but not their corresponding 
2D networks. Overall, our findings provide evidence for the utility of categorical 
colour representation in several visual tasks but also indicating a portion of categorical 
colour perception can only be explained by the language component, reconciling both universal 
and relative theories.

### Source code

The source code to train and test networks is publicly available in our
GitHub repository [DeepTHS](https://github.com/ArashAkbarinia/DeepTHS).

The experimental materials are also publicly available upon request. Due
to their large size (about 306MB for one layer, 1.8GB for one network), 
they are not uploaded to GitHub.



## Rainbow

There are no discontinuities in the electromagnetic spectrum of the light reaching us 
from a rainbow and yet we see hues clearly separated by colour categories.

To make this more tangible, we can simulate a rainbow and check the numerical values
of its constituent hues.

### Hue circle in HSV colour space

We create a list of 180 hues with constant saturation and values.

We convert the `rainbow_hues` from *HSV* colour space to *RGB* for visualisation
purposes. We can observe that the continuous function of hues appears to be separated
into different categories. This separation stems from our perceptual system
otherwise the HSV colour space is only an alternative representation of the
RGB space that is obtained from camera sensitivity functions.


<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_15_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


### Coloured arches

The visualisation of the hue circle does not have a spatial resolution (i.e., only one row),
to better appreciate the categorical colour phenomenon, we convert the hue circle into
an image of coloured arches, similar to natural rainbow.

When we illustrate coloured arches, we can clearly see colour categories such as
(from bottom to top):
1. pink
2. purple
3. blue
4. cyan
5. green
6. yellow
7. orange
8. red

Although to different observers the actual colour names and the number of distinct
colour categories might differ, but the principle remains the same, everyone sees
the continuous function in discrete categories.

    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_19_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


### Open questions

This is a fascinating phenomenon that raises the following questions:
1. Why do we perceive a continuous function in different categories?
2. Are these categories shared among everyone or are there significant
   individual differences?
3. Is the categorical colour perception because of linguistic terms we
   assign to colours and/or this is purely driven by our visual system?

In this project, we used deep neural networks as a framework to study some
aspects of categorical colour perception:
1. We compare **multimodal vision-language** to **unimodal vision** deep
   neural networks to investigate **the role of language**.
2. We compare 24 networks pretrained on an identical dataset for 24 distinct
   tasks to investigate **the role of visual tasks**.
3. We compare two **convolutional neural networks (CNN)** to **vision
   transformers (ViT)** to investigate **the role of architecture**.
4. We compare representation at different **intermediate layers** to investigate
   whether this is **low-, mid, or high-level** representation.

## Stimuli

In this section we describe the stimuli set we used to evaluate networks.

### Munsell chips

We use 320 *Munsell chips* to evaluate our networks. These chips have been extensively
used in the literature of categorical colour perception.
    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_24_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    

### Human data

We rely on human-data for **8** chromatic colour categories *(Berlin & Kay, 1969; Sturges & Whitfield, 1995)*.


    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_26_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 

    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_27_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


### Shapes

We generated 2905 shapes by systematically changing five parameters of
superellipse equation:

$
r = \left( |\frac{cos(\theta)}{a}|^{n} + |\frac{sin(\theta)}{b}|^{n} \right)^{\frac{-1}{n}}
$

The idea behind using a systematic geometrical shape is to investigate the interaction
between object shape and colour perception. This is beyond the scope of this notebook
and is part of another project.

We can plot 25 of those superellipses randomly.
    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_30_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


## Experiments

### Language models: zero-shot evaluation

For the language models (i.e., **CLIP**) we can directly conduct psychophysics
on the network without any intermediate step:
* For each shape, we colour it with a Munsell chip and input the network
  with eight phrases corresponding to eight colour terms.
* The phrase: **"This is a {COLOUR-TERM} shape."** and *COLOUR-TERM* is one of
  these terms: **red, orange, yellow, brown, green, blue, purple, pink**.
* Network's output is a number (the probability of the phrase matching the image).
  We take the phrase with the highest probability as the network's final output.
* For each Munsell chip, we repeat this procedure for all shapes (2905),
  performing **23,240 trials** ($8\times 2905$).

Let's look at one example with simulated data. In this example, the network's output
is highest for the phrase **"This is a red shape."**, therefore we take that as
the network has placed this colour into the red category. The average across all 2905
shapes would be the final prediction of the network for this colour.

    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_33_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


### Vision models: odd-one-out linear classifier

It is impossible to directly ask a neural network trained on a task like object 
recognition about colour categories, as the neural network was specifically 
trained for another task. To overcome this, we trained a linear classifier to 
perform a 4AFC colour discrimination task and at test time evaluate whether
this discrimination is categorical. That is to say, the framework to evaluate 
the categorical colour perception in vision models consists of two steps:
1. A network is trained on an arbitrary visual task (e.g., object recognition).
   We refer to such a network as a **pretrained network**.
2. Features extracted from the **frozen** pretrained network are input to a linear
   classifier trained for the colour discrimination 4AFC task. We refer to
   the trained linear classifier as a **colour-discriminator**.

#### Training colour-discriminator

The figure below shows the schematics of our training process.

<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/colour_discriminator.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 

The process of extracting features (also known as, readouts) from a pretrained 
network can occur at any depth of a network. We extract features from six distinct
layers from the early to final layer:
 * Common to all architectures: `fc` for *ImageNet* (classification layer) or `encoder`
   for *Taskonomy* (the final encoding layer) and *CLIP* (the final vision layer).
 * In the case of `ResNet50` architecture, from 5 intermediate areas (a collection
   of residual blocks).
 * In the case of `ViT-B32` from blocks `[1, 4, 7, 10, 11]`.

#### Train images

During the training, the linear classifier is input with four images:
 * Three of those are identical.
 * One odd image that only differs in colour.

The colour difference between common-odd images is drawn from a random uniform
distribution ensuring no colour bias is introduced in the colour discriminator
training.

The background colour is always achromatic whose luminance is drawn from a random
uniform distribution
    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_37_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### Testing paradigm

At test time, for each Munsell chip, we evaluate against all sets of focal colour pairs. 
For instance, for the `munsell_chips[3][2]`, we input the network with the following four
colours:
 * The first and last being one focal colour (in this example pink and red categories).
 * The two middle images are identical to the colour of the test chip.

We interpret the results:
1. If the network outputs the pink image as odd, we conclude that the network has put the
   test chip into the **red category**.
2. If the network outputs the red image as odd, we conclude that the network has put the
   test chip in the **pink category**.

We also test the network by swapping the first and last images to ensure the results are
not biased towards a certain index.

    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_39_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


For the same test chip, we repeat this procedure for all 28 combinations of pairs of focal colours:

<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/test_paradigm.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 

We assign the colour that wins the most trials across all tests/shapes as the colour of the test
chip.

### Pretrained networks

Architectures:
* **Vision Transformers (ViT)** – *ViT-B32*
* **Convolutional Neural Networks (CNN)** – *ResNet50*

Pretrained task:
* **CLIP**: multimodal text-image matching
* **ImageNet**: unimodal object classification
* **Taskonomy**: 24 unimodal tasks (e.g., scene segmentation, object recognition, edge detection, denoising, etc.).

Inetrmediate layers: six distinct layers corresponding to low-, mid- and high-level visual representation.

## Results

To better understand the data crunch from raw data to plotted figures, we look
at one example.

### Explaining with one example

We will look at the results of *Block-10* of the *ViT-B32* architecture (i.e.,
the image encoder of CLIP). The directory name `bg128_i0` means the linear classifier
(colour discriminator) has been trained with images of grey background ($R=G=B=127$).

The results are loaded into an array of shape `(320, 8, 8)`: essentially the 320
confusion matrices of size $8 \times 8$.

#### One Test chip

We can simply print the confusion matrix for one particular Munsell chip. We do that
for **chip at index 122** which corresponds to the test colour we visualised when explaining
the testing paradigm:

0. Each cell is the percentage of time a focal colour was selected as the odd element (i.e.,
   lost the categorical battle to another focal colour).
2. The diagonal of the matrix is 0.
3. Higher values indicate strong categorical representation (e.g., orange versus all other colours).
   A value close to 0.50 indicates a chance level and no categorical representation.
5. The confusion matrix cannot be reduced to the (upper/lower) triangle. The sum of $C + C^T \leq 1$,
   where $C$ and $C^T$ denote the confusion matrix and its transpose. Their sum is not guaranteed to
   equal 1, as the selected odd index by the network can also be the identical test chip. Small numbers
   for $C + C^T$ indicate the network's representation is not categorical. Overall, it can be
   observed that the $C + C^T$ is quite close to 1.

We compute the *average* winning rate of each focal colour and the highest value is
selected as the colour of the test chip.:
* In this example *orange* wins against other focal colours $95\%$ of the time.
* Note that the *average* column is not a true probability distribution, the sum is not equal
  to 1.
* A value of 0.50 indicates no categorical representation.
    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_50_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### All chips

We compute the colour of each Munsell chip following the procedure above. We can plot this
in the same format as the original Munsell image.

The plotted figure can be interpreted as follows:
* Those cells with a white colour do not have ground truth, therefore excluded.
* Other cells have taken a focal colour according to the network prediction.
    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_55_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 


We can compute the accuracy with respect to the ground truth. In this example, the network
predicts human data $83\%$ of time.


We plot **x** on top of the cells where the network's prediction mismatch the human data:


<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_60_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    

### Baseline – RGB Model

To put the obtained results with networks into perspective we compare them to 
the "RGB Model" that assigns the closest colour category (smallest Euclidean 
distance) to a Munsell chip:

 0. Eight focal colours are selected by taking the average of all Munsell chips
    in the Berlin & Kay (1969) and Sturges & Whitfield (1995) Ground Truth.
 1. For each Munsell chip, we compute the Euclidean distance to eight focal colours. 
 2. The focal colour with the smallest Euclidean distance is selected as the
    colour category of that test chip.

In simple words, if the test chip is physically closest in the space to the pink
category, its colour category will be pink.

One might argue that step 0 is not an accurate estimation of focal colours as
the centre of mass does not necessarily determine the focal colour. 
Our rationale behind  this baseline:
 
 * The RGB Model categorises colours uniformly based on proximity.
 * Essentially, in any colour space there is an inherent categorical effect
   of uniform discretisation.
 * Therefore, any categorical effect we observe in the network is significant
   if it surpasses the RGB Model.

We computed the physical proximity in several colour spaces, including:
 * DKL
 * CIE L\*a\*b\*
 * RGB
 * LMS
 * HSV
 * YP<sub>b</sub>P<sub>r</sub>

We have taken RGB as the baseline because of two reasons:
 * The pattern of results across colour spaces is very similar.
 * The input colour space to networks is RGB (i.e., the pretrained datasets are in RGB).
   Therefore we can analyse how much the colour categories alter from the
   input representation to the network's internal representation.

### The role of language

To assess the role of language on categorical colour perception, we compare
the results of two sets of networks pretrained on **CLIP** and **ImageNet**:

|   | CLIP (Multimodal language-vision) | ImageNet (Unimodal vision) |
|---|---|---|
| Vision Transformer (ViT) – ViT-B32  |   |   |
| Convolution Neural Network (CNN) – ResNet50 |   |   |

For each of these networks, we have trained several instances to ensure the
reported results are robust. Given the high degree of similarity across
instances, below we visualise the results for instance 1.



#### CLIP - ViT-B32

    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_66_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### CLIP - ResNet50


    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_68_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### ImageNet - ViT-B32


    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_70_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### ImageNet - ResNet50


    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_72_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### Multimodal language-vision vs. Unimodal vision
    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_74_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


### The role of visual task

In this section, we examine how the network's task shapes its colour categories using the [Taskonomy dataset](http://taskonomy.stanford.edu/), which contains about four million images (mainly indoor scenes from 2265 different buildings) and their corresponding labels for 25 computer vision tasks. The dataset also provides pretrained networks with an encoder-decoder architecture for all visual tasks. The encoder is the same across all pretrained networks (i.e., ResNet50), which maps the input image ($224 \times 224$) into a latent representation of size 1568 ($14 \times 14 \times 8$). The decoder design varies according to the dimensionality of the task output. The encoder offers a unique opportunity to study the role of visual tasks on the representation a network learns, given its architecture is identical across tasks and has been trained on the same set of images. Similar to ImageNet pretrained networks, we trained a linear classifier on top of the encoder's extracted features from each Taskonomy pretrained network.


#### Munsell prediction



<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_1.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_2.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_3.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_4.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_5.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_6.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_7.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_8.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_9.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_10.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_11.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_12.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_13.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_14.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_15.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_16.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_17.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_18.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_19.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_20.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_21.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_22.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_23.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_78_24.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


#### Comparison across tasks



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_81_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    


## Discussion

* **Unimodal vision** models explain 85% of human data.
* The remaining 15% is explained by **multimodal vision-language** models.
* Categorical colour perception is a **free-from-language representation**, although its **development** is influenced by **linguistic terms**.



    
<div class="row">
	<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DeepReconciliationOfCategoricalColourPerception/output_83_0.png" class="img-fluid rounded z-depth-1" %}	
    </div>
</div> 
    
