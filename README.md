## Summary

> **Original Gigantum Project: [https://gigantum.com/dmk/gtc2021](ttps://gigantum.com/dmk/gtc2021)**
>
> [Download](https://gigantum.com/download) Gigantum to run this Project on your own hardware with a minimal effort.

This repo is an export from the [Gigantum Project](https://docs.gigantum.com/docs/projects) used in the demo from the GTC 2021 session "IMPROVE REPRODUCIBILITY AND PORTABILITY OF DATA SCIENCE WORKFLOWS FROM A MOBILE WORKSTATION TO THE CLOUD" presented by Dean Kleissas. It is intended for non-Gigantum users to manually reproduce the demo and may require extra manual steps to get working properly since the environment is not managed for you.

You can view the session here (link to be added)

## Installation

1) Start with a virtualenv and CUDA 10 support. 
2) Install nodejs
3) Install python dependencies via `pip install -r requirements.txt`
4) run `jupyter labextension install @jupyter-widgets/jupyterlab-manager`

If you wish to run the contents of this Project on a CPU instead of a GPU you must install the `tensorflow` package instead of `tensorflow-gpu`. 

## Demo Objective
The object of this demo was to take an existing model and apply it to a new dataset. The model classifies pixels as "membrane" or "non-membrane" in electron microscopy images of mouse cortext. The new dataset is from a different part of the mouse brain and imaged under different conditions. The majority of the demo was done on a laptop with an RTX5000.

## Existing Model
The first part of the demo was to get an existing model and code working. This was imported from existing work done by the team at JHU/APL. Because the code and model is a bit old work was needed to get everything functioning. The notebook `membrane_detection-kasthuri11.ipynb` exercises the existing model on the original dataset, making sure everything is working.

## New Data and Training
The next part of the demo was to create new training data and apply some more training to the pretrained model. A small training set is inspected and prepared in `data_prep.ipynb` and training done in `membrane_train.ipynb`

## Inference
Finally, the trained model was applied to 25GB of data. This step was done in AWS on a p3.16xlarge with 8 GPUs. For this step, the `inference-runner.ipynb` notebook is used to drive parallel jobs via [papermill](https://papermill.readthedocs.io/en/latest/)

## Acknowledgements
The pre-trained model and some of the imported code (files in the `saber` directory) was originally derived from the [SABER repository](https://github.com/aplbrain/saber) and provided with an Apache-2.0 License. The SABER software system was designed and developed by the Johns Hopkins University Applied Physics Laboratory (JHU/APL).