# Cell-Segmentation
This is respository includes pytorch implementation of cell segmentation algorithms Unet, DoubleUnet, Swin-Unet and Cell pose with preprocesing steps for wholeslide ndpi images
## Installation 
Download the zipfile and unzip in your python environment, code can be either run from command line using python main.py  or with shell script main.sh
### Install dependencies
Run install.sh or install dependencies/python libraries manualy in your environment. 

### Directory Structure
~~~
|-- data
|-- eval
|   |-- evaldoubleunet.py
|   |-- evalswinunet.py
|   |-- evalunet.py
|-- install.sh
|-- loader
|   |-- bart_dataset.py
|   |-- color2black.py
|   |-- datareader.py
|   |-- datasets_old.py
|   |-- datasets.py
|   |-- glas_dataset.py
|-- log
|-- loss
|   |-- dice.py
|-- main.py
|-- main.qsub
|-- models
|   |-- doubleunet.py
|   |-- swinunet.py
|   `-- unet.py
|-- output
|-- train
|   |-- traindoublnet.py
|   |-- trainswinunet.py
|   `-- trainunet.py
|-- util
|   |-- seg_trans.py
|   |-- swinunetconfig.py
|   `-- testmetric.py
|-- weights
|   |-- doublenet_256x256_V1.0.wth
|   |-- swinunet_224x224_V1.0.wth
|   |-- unet_256x256_V1.0_pannuke.wth
|   `-- unet_256x256_V2.0_pannuke_full.wth
~~~
