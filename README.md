## Visual question answering (VQA) approach to explaining autonomous driving actions

In this repository, we provide the first empirical study on explaining autonomous driving actions using a visual question-answering approach. Given an action performed by a self-driving car within a driving scene and a question asked about such an action, the VQA framework should predict a correct and intelligible justification (i.e., answer) for that chosen action.  
## Setup

Firstly, we need to get the MS COCO files. In order to get the MS COCO files, we need to go to  the ```src/utilities``` folder and execute ``` download_and_unzip_datasets.csh ```. The commands inside this script file will download the MS COCO images. Once this step is completed,  execute the ```make_vocabs_for_questions_answers.py``` file. This script will generate the question and answer vocabularies for the MS COCO images.

The next step is to train the VQA network on the MS COCO images using the ```src/vqa_notebook_train_MSCOCO.ipynb``` script and save the PyTorch model. It took us nearly ~ 36 hours to train the MS COCO images with 50 epochs on a machine with a NVIDIA RTX 3090 GPU and a 32 GB memory size.   

## Dataset Construction
To obtain driving data, we ran the [Deep Deterministic Policy Gradient (DDPG)](https://arxiv.org/pdf/1509.02971.pdf) algorithm on [CARLA 0.9.11](https://carla.readthedocs.io/en/0.9.11/). While an autonomous car was operating in its environment, we recorded its driving video that shows the vehicle's field of view (FoV) in each instantaneous step. We then convert the collected driving video to image sequences uniformly, and annotate the actions performed in each driving scene (i.e., frame) with question-answer pairs. Thus, our dataset consists of three parts:

**Training Data:** 250 frames from the autonomous car's driving on  Town 1 (```VQA-AD/src/Training Data/```)  <br>
**Test Data:** 100 frames from the autonomous car's driving on Town 1 and Town 2 (```VQA-AD/src/Testing Data/```) <br> 
**VQA Annotation:** CSV files that contain question-answer pairs, and image paths (```VQA-AD/src/VQA annotations/```).
