## Visual question answering (VQA) approach to explaining autonomous driving actions

In this repository, we provide a preliminary study of explaining autonomous driving actions using a visual question-answering approach. The goal is that, given an action performed by a self-driving car within a driving scene and a question asked about such an action, the VQA framework should provide a correct and intelligible justification (i.e., answer) for that chosen action.  

## Setup

Firstly, we need to get the MS COCO files. In order to get the MS COCO files, we need to go to  the ```src/utilities``` folder and execute ``` download_and_unzip_datasets.csh ```. The commands inside this script file will download the MS COCO images. Once this step is completed,  execute the ```make_vocabs_for_questions_answers.py``` file. This script will generate the question and answer vocabularies for the MS COCO images.

The next step is to train the VQA network on the MS COCO images using the ```src/vqa_notebook_train_MSCOCO.ipynb``` script and save the PyTorch model. It took us nearly ~ 40 hours to train the MSCOCO images with 50 epochs on a machine with a NVIDIA RTX 3090 GPU and 32 GB memory size.   
