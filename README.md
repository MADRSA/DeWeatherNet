# DeWeatherNet


Note: This code base is still not complete. The DeWeatherNet model can be found in this code-base. Please feel free to take the model file and run it with your train/eval. Train and Eval scripts for this code-base will be updated later when I have time. Sorry for the incovenience.


### About this repo:

This repo hosts the implentation code for "DeWeatherNet". We also provide code for a strong transformer baseline for weather removal tasks.

## Introduction

Removing adverse weather conditions like rain, fog, and snow from images is an important problem in many applications. Most methods proposed in the literature have been designed to deal with just removing one type of degradation. Recently, a CNN-based method  using neural architecture search (All-in-One) was proposed  to remove all the weather conditions at once. However, it has a large number of parameters as it uses multiple encoders to cater to each weather removal task and still has scope for improvement in its performance. In this work, we focus on developing an efficient solution for the all adverse weather removal problem. To this end, we propose DeWeatherNet, a transformer-based end-to-end model with just a single encoder and a decoder that can restore an image degraded by any weather condition. Specifically, we utilize a transformer encoder using intra-patch transformer blocks to enhance attention inside the patches to effectively remove smaller weather degradations. We also introduce a transformer decoder with learnable weather type embeddings to adjust to the weather degradation at hand. DeWeatherNet achieves significant improvements across multiple test datasets over both All-in-One network as well as methods fine-tuned for specific tasks. 


## Using the code:

- Clone this repository:
```bash
git clone https://github.com/MADRSA/DeWeatherNet
cd DeWeatherNet
```

To install all the dependencies using conda:

```bash
conda env create -f environment.yml
conda activate DeWeatherNet
```


## Datasets:

### Train Data:

DeWeatherNet is trained on a combination of images sampled from Outdoor-Rain, Snow100K, and Raindrop datasets (similar to [All-in-One (CVPR 2020)](https://openaccess.thecvf.com/content_CVPR_2020/papers/Li_All_in_One_Bad_Weather_Removal_Using_Architectural_Search_CVPR_2020_paper.pdf)), dubbed as "All-Weather", containing 18069 images. It can be downloaded from this [link](https://drive.google.com/file/d/1tfeBnjZX1wIhIFPl6HOzzOKOyo0GdGHl/view?usp=sharing).


### Dataset format:

Download the datasets and arrange them in the following format. T
```
    DeWeatherNet
    ├── data 
    |   ├── train # Training  
    |   |   ├── <dataset_name>   
    |   |   |   ├── input         # rain images 
    |   |   |   └── gt            # clean images
    |   |   └── dataset_filename.txt
    |   └── test  # Testing         
    |   |   ├── <dataset_name>          
    |   |   |   ├── input         # rain images 
    |   |   |   └── gt            # clean images
    |   |   └── dataset_filename.txt
```

### Text Files:

[Link](https://drive.google.com/file/d/1UsazX-P3sPcDGw3kxkyFWqUyNfhYN_AM/view?usp=sharing)


## Extensions:

Note that DeWeatherNet is built to solve all adverse weather problem with a single model. We observe that, additionally DeWeatherNet can be easilty modified (removing the transformer decoder) to just focus on an individual restoration task. 

### Acknowledgements:

This code-base uses certain code-blocks and helper functions from [Syn2Real](https://github.com/rajeevyasarla/Syn2Real), [Segformer](https://github.com/NVlabs/SegFormer), and [ViT](https://github.com/lucidrains/vit-pytorch).

```
