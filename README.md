# Cell-Segmentation
This is respository includes pytorch implementation of cell segmentation algorithms Unet, DoubleUnet, Swin-Unet and Cell pose with preprocesing steps for wholeslide ndpi images
## Installation 
Download the zipfile and unzip in your python environment, code can be either run from command line using python main.py  or with shell script main.sh
### Install dependencies
Run install.sh or install dependencies/python libraries manualy in your environment. 

### Directory Structure
~~~
|-- data  (Optional data folder, data folders can be update in shell script or passed through  command line) 
|-- eval (This package consists evaluation classes for implemented models) 
|   |-- evaldoubleunet.py     
|   |-- evalswinunet.py
|   |-- evalunet.py
|-- install.sh
|-- loader ((This package consists data loader classes implemented various data sets used.) 
|   |-- bart_dataset.py
|   |-- color2black.py
|   |-- datareader.py
|   |-- datasets_old.py
|   |-- datasets.py
|   |-- glas_dataset.py
|-- log 
|-- loss
|   |-- dice.py
|-- main.py   (Python enty poin for the code, run this with required argument) 
|-- main.qsub ( A qsub scrip consiting shell commands ) 
|-- models  ((This package consists classes for implemented models) 
|   |-- doubleunet.py
|   |-- swinunet.py
|   `-- unet.py
|-- output
|-- train (This package consists training classes for implemented models) 
|   |-- traindoublnet.py
|   |-- trainswinunet.py
|   `-- trainunet.py
|-- util (This package consists utility methods/classes used in the project) 
|   |-- seg_trans.py
|   |-- swinunetconfig.py
|   `-- testmetric.py
|-- weights (This folder consists trained weights of diffrent segmentation methods ) 
|   |-- doublenet_256x256_V1.0.wth
|   |-- swinunet_224x224_V1.0.wth
|   |-- unet_256x256_V1.0_pannuke.wth
|   `-- unet_256x256_V2.0_pannuke_full.wth
~~~


### Directory Structure for Datasets
Datasets need to follow below directory structure to work 
~~~
.
|-- bart
|   |-- bart_metadata.csv
|   |-- images
|   |   |-- CD3\ CD20\ TMA\ C\ COLUMN\ 1\ 20220510.ndpis_Region0_0_0_0.png
|   |-- masks
|   |   |-- CD3\ CD20\ TMA\ C\ COLUMN\ 1\ 20220510.ndpis_Region0_0_0_0.png
|-- GlaS
|   |-- Grade.csv
|   |-- test
|   |   |-- image
|   |   |   |-- testA_10.bmp
|   |   `-- mask
|   |       |-- testA_10_anno.bmp
|   `-- train
|       |-- image
|       |   |-- train_10.bmp
|       `-- mask
|           |-- train_10_anno.bmp
|-- PanNuke
|   |-- fold_1.zip
|   |-- fold_2.zip
|   |-- fold_3.zip
|   |-- folds
|   |   |-- images
|   |   |   |-- fold1
|   |   |   |   |-- Breast.jpeg
|   |   |   |   |-- images.npy
|   |   |   |   `-- types.npy
|   |   |   |-- fold2
|   |   |   |   |-- images.npy
|   |   |   |   `-- types.npy
|   |   |   `-- fold3
|   |   |       |-- images.npy
|   |   |       `-- types.npy
|   |   `-- masks
|   |       |-- fold1
|   |       |   |-- Breast.jpeg
|   |       |   `-- masks.npy
|   |       |-- fold2
|   |       |   `-- masks.npy
|   |       `-- fold3
|   |           `-- masks.npy
|   `-- inflate.py

~~~
