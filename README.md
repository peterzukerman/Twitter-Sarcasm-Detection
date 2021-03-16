<h1 align="center">
  <br>
  <a href="https://github.com/dheerajpatta/CourseProject/blob/main/documentation/Twitter%20Sarcasm%20Classification%20Competition.pdf"><img src="https://github.com/dheerajpatta/CourseProject/blob/main/images/Twitter%20Sarcasm.png" alt="Twitter Sarcasm Classification" width="1000"></a>
</h1>

<h4 align="center">Our solution and winning model for the Coursera Text Classification Competition</h4>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a></li>
	<li><a href="#project-repository-structure">Project Repo Structure</a></li>
    <li><a href="#our-approach">Our Approach</a></li>
	<li><a href="#understanding-data">Understanding Data</a></li>
	<li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
	<li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#references">References</a></li>
  </ol>
</details>

# Text Classification Competition: Twitter Sarcasm Detection 
# About the Project
The goal of this competition/project is to classify a given sequence of tweets (responses) as sarcastic or non-sarcastic. The tweets with its corresponding immediate context 
and full context is provided as continous responses to each tweets.The tweets are provided with conversation context which is an ordered list of dialogue. The objective of this competition is to predict the “label” of the response (tweets) using the given context (either immediate or full context) 

We present our best model based on **BERT** (Bi-directional Enconding Representations from Transfomers) using pre-trained stock weights of BERT-Base model and demonstrate the winning solution able to classify sarcasm with F1-score of 76.09%.

# Project Repository Structure

Please follow the links to navigate to respective folders -
- [Data](https://github.com/dheerajpatta/CourseProject/tree/main/data)
- [Source Code](https://github.com/dheerajpatta/CourseProject/tree/main/models)
- [Results](https://github.com/dheerajpatta/CourseProject/tree/main/sarcasm%20results)
- [Documentation](https://github.com/dheerajpatta/CourseProject/tree/main/documentation)
	- [Proposal](https://github.com/dheerajpatta/CourseProject/tree/main/documentation/project%20proposal)
	- [Progress Report](https://github.com/dheerajpatta/CourseProject/tree/main/documentation/progress%20report)
	- [Video Presentation](https://github.com/dheerajpatta/CourseProject/blob/main/documentation/Twitter%20Sarcasm%20Classification%20Competition%20-%20Video%20Presentation%20Links.pptx)
	- [Long Form Video Link](https://mediaspace.illinois.edu/media/t/1_lbmrkxnd)
	- [Short Form Video Link](https://mediaspace.illinois.edu/media/t/1_8an3avdx)
	- [Detailed Project Presentation](https://github.com/dheerajpatta/CourseProject/blob/main/documentation/Twitter%20Sarcasm%20Classification%20Competition.pdf)

# Our Approach
<a href="https://github.com/dheerajpatta/CourseProject/blob/main/documentation/Twitter%20Sarcasm%20Classification%20Competition.pdf"><img src="https://github.com/dheerajpatta/CourseProject/blob/main/images/Approach.png" alt="Approach" width="1000"></a>

# Understanding Data:

Each line contains a JSON object with the following fields : 
- ***response*** :  the Tweet to be classified
- ***context*** : the conversation context of the ***response***
	- Note, the context is an ordered list of dialogue, i.e., if the context contains three elements, `c1`, `c2`, `c3`, in that order, then `c2` is a reply to `c1` and `c3` is a reply to `c2`. Further, the Tweet to be classified is a reply to `c3`.
- ***label*** : `SARCASM` or `NOT_SARCASM` 

- ***id***:  String identifier for sample. This id will be required when making submissions. (ONLY in test data)

For instance, for the following training example : 

`"label": "SARCASM", "response": "@USER @USER @USER I don't get this .. obviously you do care or you would've moved right along .. instead you decided to care and troll her ..", "context": ["A minor child deserves privacy and should be kept out of politics . Pamela Karlan , you should be ashamed of your very angry and obviously biased public pandering , and using a child to do it .", "@USER If your child isn't named Barron ... #BeBest Melania couldn't care less . Fact . 💯"]`

The response tweet, "@USER @USER @USER I don't get this..." is a reply to its immediate context "@USER If your child isn't..." which is a reply to "A minor child deserves privacy...". Your goal is to predict the label of the "response" while optionally using the context (i.e, the immediate or the full context).

***Dataset size statistics*** :

| Train | Test |
|-------|------|
| 5000  | 1800 |

# Getting Started
All our models are in notebook format (.ipynb) and can be easily replicated using Jupyter / Google Colab or any other notebook environment.
We recommend anaconda distribution to create virtual environments for Python and recommend Google Colab for TensorFlow (TF)/Keras
Implementations.

In order to replicate, reproduce or rerun our BERT model, we recommend downloading pre-trained stock weights as given below

# Built With
- [Python](https://www.python.org/)
- [Google Colab](https://colab.research.google.com/)
- [Keras](https://keras.io/)
- [TensorFlow](https://www.tensorflow.org/)

# Prerequisites
1. Git
2. Python 3.6 or above.
3. Jupyter or Anaconda distribution
4. Google Colab
5. TensorFlow GPUs
6. Keras
7. BERT Pre-trained Stock Weights.
You can download and use pre-trained stock weights of BERT-Base Model from [here](https://storage.googleapis.com/bert_models/2018_10_18/uncased_L-12_H-768_A-12.zip)

# Installations

Following packages/libraries are required for fully functioning of our BERT Model -
```bash
# install data pre-processing libraries
$ pip install genism
$ pip install ekphrasis
```

Install/Import the necessary libraries and frameworks
```bash
# Install key libraries and frameworks
$ pip install tensorflow-gpu
$ pip install --upgrade grpcio
$ pip install tqdm
$ pip install bert-fo-tf2
```

Install/Import the necessary libraries and frameworks
```bash
# Import the following packages/libraries/frameworks
>> import pandas as pd
>> import numpy as np
>> import tensorflow as ft
>> from tensorflow import keras

>> import bert
>> from bert import BertModelLayer
>> from bert.loader import StockBertConfig, map_stock_config_to_params, load_stock_weights
>> from bert.tokenization.bert_tokenization import FullTokenizer
```

Install/Import the necessary evaluation metrics
```bash
>> from sklearn.metrics import confusion_matrix, classification_report
>> from sklearn import preprocessing
```

Download pre-trained weights from BERT-Base model
```bash
>> !wget https://storage.googleapis.com/bert_models/2018_10_18/uncased_L-12_H-768_A-12.zip
>> !unzip uncased_L-12_H-768_A-12.zip
```

# Usage
To clone and run our model, you'll need [Git](https://git-scm.com) or git GUI clients like [Git Kraken for Windows](https://www.gitkraken.com/download/windows64) or [Tower for Mac](https://www.git-tower.com/mac) and [Python](https://www.python.org/downloads/)

From your command line or terminal application or git client:

```bash
# Clone this repository
$ git clone https://github.com/dheerajpatta/CourseProject.git

# Go into the repository
$ cd models

# Install above prerequisties and dependencies
# pip install *

# Run the Jupyter Notebook
# https://github.com/dheerajpatta/CourseProject/blob/main/models/sarcasm_classification_bert_large.ipynb
```
Additional References -
- Google [Colab](https://colab.research.google.com/)
- All about setting up Google Colab  like a Pro from [here](https://medium.com/@robertbracco1/configuring-google-colab-like-a-pro-d61c253f7573)
- If you want to use BERT with Colab, you can get started with the notebook [BERT FineTuning with Cloud TPUs](https://colab.research.google.com/github/tensorflow/tpu/blob/master/tools/colab/bert_finetuning_with_cloud_tpus.ipynb?_sm_au_=isVs7pNrsWJRkDtjVsBFjK664v423)

# Contact
- Artsiom Strok (astrok2@illinois.edu)
- Peter Zukerman (peterz2@illinois.edu)
- Dheeraj Patta (npatta2@illinois.edu)

# License
Our solution for Text Classificaiton competition - Twitter Sarcasm Detection is licensed under the terms of the GPL Open Source license and is available for free.
