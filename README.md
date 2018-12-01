# pytorch-image-classification

Image classification in pytorch on Cifar and Imagenet


## Cifar-10 


### Results

| Model            | Test data | Our Accuracy| Original Accuracy | Related paper |
|------------------|-----------|---------|------------------|--------------------|
| Resnet-20    | Cifar-10  | 0.9213 | 0.9125 |  [Deep Residual Learning](https://arxiv.org/pdf/1512.03385.pdf) |


## Imagenet

### Data preparation

1. ```sudo apt-get install aria2```

2. Navigate to ```http://academictorrents.com/collection/imagenet-2012``` and download torrent files for train and validation datasets.

3. Follow this page ```https://aria2.github.io/``` and do ```aria2c path_to_you_torrent_file.torrent``` for both validation and training files.

4. By now, you should have two files in your folder ```ILSVRC2012_img_train.tar``` and ```ILSVRC2012_img_val.tar```.

5. Run this command: 
```
mkdir train && mv ILSVRC2012_img_train.tar train/ && cd train
tar -xvf ILSVRC2012_img_train.tar && rm -f ILSVRC2012_img_train.tar
find . -name "*.tar" | while read NAME ; do mkdir -p "${NAME%.tar}"; tar -xvf "${NAME}" -C "${NAME%.tar}"; rm -f "${NAME}"; done
cd ..
```
6. And this:
```
mkdir val && mv ILSVRC2012_img_val.tar val/ && cd val && tar -xvf ILSVRC2012_img_val.tar
wget -qO- https://raw.githubusercontent.com/soumith/imagenetloader.torch/master/valprep.sh | bash
```
