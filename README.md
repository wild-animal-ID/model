# Automatic Identification of Wild Protected Animals Based on Deep Learning
## Project Introduction
Automated wildlife identification can considerably minimise the time and effort required for wildlife identification, and it can promote the development of wildlife conservation. We independently constructed a database containing 260 species of protected wildlife unique to Nanjing Agricultural University based on the Wildlife under Special State Protection List (China). The constructed database was used to test the performance of several convolutional neural networks (e.g., AlexNet, VGGNET16 and ResNet50) for animal identification. The best-performing network model, ResNet50, with a TOP-1 accuracy of 83.49% and maximum accuracy of 100% was selected for our automatic animal identification model. Finally, we developed a mobile application for the automatic identification of protected wildlife using the abovementioned database and convolutional neural network model, allowing automatic recognition of images of protected wild animals to reduce the time and effort for manual identification and improving public’s knowledge of protected wild animals. This paper provides data and technical support for future wild animal research and is crucial for promoting the monitoring and protection of wild animals.

## [Model](https://github.com/wild-animal-ID/model) 
### ConvNets:
 * [AlexNet](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)
 * [VGGNet](https://arxiv.org/pdf/1409.1556.pdf)
 * [ResNet](https://arxiv.org/pdf/1512.03385.pdf)
 
### Requirements
 * Python 3.5
 * Tensorflow-gpu 1.8
 * NumPy
 * OpenCV2
 
### Usage
#### data
 The data of each species category is under the data folder. 
 eg. `data/Mammals/train.txt` and `data/Mammals/val.txt` . 
 The format must be like following:

```
/absolute/path/to/image1.jpg class_index
/absolute/path/to/image2.jpg class_index
...
```

`class_index` must start from `0`.

> Do not forget to pass `--num_classes` flag when running `finetune.py` script.

#### code
```bash
# Go to related folder that you want to finetune
cd vggnet

# Download the weights
./download_weights.sh

# See finetuning options (there is some difference between them, like dropout or resnet depth)
python finetune.py --help

# Start finetuning
python finetune.py [options]

# You can observe finetuning with the tensorboard (default tensorboard_root_dir is ../training)
tensorboard --logdir ../training

# Start predict
python predict.py 
```

#### utils
```
preprocess.py: process the image read from the data file
```
#### code reference
https://github.com/kratzert/finetune_alexnet_with_tensorflow/


## [DataSet](https://github.com/wild-animal-ID/animal-dataset)
### Species catalog.xls
An excel file that contains the list of species in the database, including the list of recognisable species and the list of species that were excluded from the training of the model (unrecognisable species).
### Characteristic information of wild protected animals.xlsx
An excel file that contains detailed information of all protected wildlife in China
### Image database
Uploaded to [Google Drive](https://drive.google.com/drive/folders/1G0jq1EJsvc0nekqKS8Dv7LEsvNktr6_D?usp=sharing)

## Acknowledgements
College of Information Management, Nanjing Agriculture University, Nanjing, People’s Republic of China

    
 
 