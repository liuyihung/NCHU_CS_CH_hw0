# deep learning CNN model for 70 dog sata set
this data is from [70 dogs Breeds](https://www.kaggle.com/datasets/gpiosenka/70-dog-breedsimage-data-set/data)  
with refrence: [work1](https://www.kaggle.com/code/harshpriye/dogs-breed-prediction-cnn-inceptionv3) and [reference2](https://keras.io/api/applications/) and[Rethinking the Inception Architecture for Computer Vision](https://arxiv.org/abs/1512.00567)  

## this code is run on colab, also with other work(CNN: file name=) but with poor performance due to hardware source limit, but also upload in same folder

這個模型使用了InceptionV3, 為keras所包含的pre trained model之一，一開始的輸入為non trainable的InceptionV3 model，最後會將輸出結果輸入到一Global average Pool layer，Global Average Pool layer的功能為
