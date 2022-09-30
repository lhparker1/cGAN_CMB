# cGAN-CMB
This repository contains the code for the paper titled "Recovering Galaxy Cluster Convergence from Lensed CMB with Generative Adversarial Networks." Specifically, this repository includes the code to process simulations of lensed CMB, tSZ, kSZ, and kappa maps around desired galaxy clusters, to build and train a ResUNet and Pix2Pix cGAN, and to evaluate these models' performances. 

## Installs
For Websky database construction:
- Python >=3.7
- Orphics (https://github.com/msyriac/orphics)
- Pixell (https://github.com/simonsobs/pixell)
- Healpy (https://github.com/healpy/healpy)

For model training and evaluation:
- Python >=3.7
- Tensorflow >= 2.0
- Orphics

## Instructions
In order to build the Websky datasetes used for network training and evaluation, you will first need to download the relevant maps from the Websky database, which can be found at: https://mocks.cita.utoronto.ca/index.php/WebSky_Extragalactic_CMB_Mocks. 

From these maps, you can construct desired pure CMB, astrophysical noised (tSZ/kSZ) CMB, and 5uk/arcmin noised CMB maps and their corresponding kappa maps for galaxy clusters using the code available in websky_database_construction. The output will be a dataset of flat 2D numpy arrays representing 128x128 arcmin squares around the cluster center at a resolution of 1 pixel per arcmin to be fed into the models during training.  

The code used to train both the ResUNet and the cGAN models can be found in model_training_and_testing. This code will take the relevant numpy arrays from wherever you stored them during construction, and train either hte ResUNet or the cGAN. This file also contains the code used to evaluate the models' performance, i.e. visualize outputs for a sample cluster/generate power spectra/generate one-point PDFs.  

