<<<<<<< HEAD
fpn.pytorch
Pytorch implementation of Feature Pyramid Network (FPN) for Object Detection

## Introduction

This project inherits the property of our [pytorch implementation of faster r-cnn](https://github.com/jwyang/faster-rcnn.pytorch). Hence, it also has the following unique features:

* **It is pure Pytorch code**. We convert all the numpy implementations to pytorch.

* **It supports trainig batchsize > 1**. We revise all the layers, including dataloader, rpn, roi-pooling, etc., to train with multiple images at each iteration.

* **It supports multiple GPUs**. We use a multiple GPU wrapper (nn.DataParallel here) to make it flexible to use one or more GPUs, as a merit of the above two features.

* **It supports three pooling methods**. We integrate three pooling methods: roi pooing, roi align and roi crop. Besides, we convert them to support multi-image batch training.

## Benchmarking

We benchmark our code thoroughly on three datasets: pascal voc, coco. Below are the results:

1). PASCAL VOC 2007 (Train/Test: 07trainval/07test, scale=600, ROI Align)

model    | GPUs | Batch Size | lr        | lr_decay | max_epoch     |  Speed/epoch | Memory/GPU | mAP 
---------|-----------|----|-----------|-----|-----|-------|--------|--------
Res-101    | 8 TitanX | 24| 1e-2 | 10  | 12  |  0.22 hr | 9688MB  | 74.2

**Results on coco are on the way**.


## Training (waiting to be added IoU-branch)


    mkdir data

    cd data

    wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtrainval_06-Nov-2007.tar

    wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtest_06-Nov-2007.tar

    wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCdevkit_08-Jun-2007.tar

    tar xvf VOCtrainval_06-Nov-2007.tar

    tar xvf VOCtest_06-Nov-2007.tar

    tar xvf VOCdevkit_08-Jun-2007.tar


    and you can get pretrained resnet101 from https://www.dropbox.com/s/iev3tkbz5wyyuz9/resnet101_caffe.pth?dl=0


