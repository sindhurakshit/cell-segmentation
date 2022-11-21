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
### Running code 
* Activate your conda environment "conda activate <your environment name>".
* Make sure that all dependencies mentioned in install.sh are installed. if Running first time you my run install.sh to ensure all dependencies are installed.
 
~~~


######################################### PANNUKE DATA SET ###########################################################################

#training Unet on PanNuke dataset
python3 main.py -a train -n unet -d pannuke -lr .00005 -batch_size 30 -epoch 400  -w unet_pannuke_256x256_v1.0.wth  --source_folder /data/home/ec211268/kumar/project/data/PanNuke/folds

#Evalualting  Unet on PanNuke dataset 
python3 main.py -a eval -d pannuke  -n unet  -w unet_pannuke_256x256_v1.0.wth  --source_folder /data/home/ec211268/kumar/project/data/PanNuke/folds


#training doubleunet on PanNuke Dataset
python3 main.py -a train -n doubleunet  -d pannuke -lr .00005 -batch_size 30 -epoch 400  -w doublenet_pannuke_256x256_V1.0.wth --source_folder /data/home/ec211268/kumar/project/data/PanNuke/folds
#Evalualting double unet 
python3 main.py -a eval -d pannuke  -n doubleunet -w doublenet_pannuke_256x256_V1.0.wth --source_folder /data/home/ec211268/kumar/project/data/PanNuke/folds

#Training swinunet on Panuke data set
python3 main.py -a train -n swinunet -d pannuke -lr .00005 -batch_size 30 -epoch 400  -w swinunet_pannuke_224x224_V1.0.wth --source_folder /data/home/ec211268/kumar/project/data/PanNuke/folds

#Evalualting swin unet on PanNuke dataset 
python3 main.py -a eval -n swinunet  -d pannuke  -w swinunet_pannuke_224x224_V1.0.wth --source_folder /data/home/ec211268/kumar/project/data/PanNuke/folds


######################################### BART DATA SET ###########################################################################
#training Unet on bart dataset
python3 main.py -a train -n unet -d bart -lr .00005 -batch_size 20 -epoch 400  -w unet_bart_256x256_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/bart

#Evalualting  Unet on bart dataset 
python3 main.py -a eval -d bart  -n unet  -w unet_bart_256x256_v1.0.wth  --source_folder /data/home/ec211268/kumar/project/data/bart


#training doubleunet on bart Dataset
python3 main.py -a train -n doubleunet  -d bart -lr .00005 -batch_size 20  -epoch 400  -w doublenet_bart_256x256_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/bart

#Evalualting double unet 
python3 main.py -a eval -d bart  -n doubleunet -w doublenet_bart_256x256_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/bart

#Training swinunet on bart  data set
python3 main.py -a train -n swinunet -d bart -lr .00005 -batch_size 20 -epoch 400  -w swinunet_bart_224x224_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/bart

#Evalualting swin unet on bart  dataset 
python3 main.py -a eval -n swinunet  -d bart  -w swinunet_bart_224x224_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/bart


######################################### GlaS DATA SET ###########################################################################

#training Unet on PanNuke dataset
python3 main.py -a train -n unet -d glas -lr .005 -batch_size 20 -epoch 400  -w unet_glas_256x256_v1.0.wth  --source_folder /data/home/ec211268/kumar/project/data/GlaS

#Evalualting  Unet on PanNuke dataset 
python3 main.py -a eval -d glas  -n unet  -w unet_glas_256x256_v1.0.wth  --source_folder /data/home/ec211268/kumar/project/data/GlaS


#training doubleunet on PanNuke Dataset
python3 main.py -a train -n doubleunet  -d glas -lr .00005 -batch_size 20  -epoch 400  -w doublenet_glas_256x256_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/GlaS

#Evalualting double unet 
python3 main.py -a eval -d glas  -n doubleunet -w doublenet_glas_256x256_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/GlaS

#Training swinunet on Panuke data set
python3 main.py -a train -n swinunet -d glas -lr .00005 -batch_size 20 -epoch 400  -w swinunet_glas_224x224_v1.0.wth --source_folder /data/home/ec211268/kumar/project/data/GlaS

~~~
