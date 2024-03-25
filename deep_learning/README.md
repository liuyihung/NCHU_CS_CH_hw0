# deep learning CNN model for 70 dog sata set
this data is from [70 dogs Breeds](https://www.kaggle.com/datasets/gpiosenka/70-dog-breedsimage-data-set/data)  
with refrence: [work1](https://www.kaggle.com/code/harshpriye/dogs-breed-prediction-cnn-inceptionv3) and [reference2](https://keras.io/api/applications/) and[Rethinking the Inception Architecture for Computer Vision](https://arxiv.org/abs/1512.00567)  

## this code is run on colab, also with other work(CNN: file name=) but with poor performance due to hardware source limit, but also upload in same folder

這個模型使用了InceptionV3, 為keras所包含的pre trained model之一，一開始的輸入為non trainable的InceptionV3 model，最後會將輸出結果輸入到一Global average Pool layer，選用Global Average Pool layer的主要理由為其可以在降低接續計算的參數量的同時(但仍然保留channel數)，藉由normalization避免over fit的現象，最後經過兩層dense layer(activation function分別為relu和softmax)，最後我們在輸出test_data.xlsx時則選擇機率最高的可能輸出作為解答。  
## discution based on valid set result
我們在訓練時使用了dataset中的valid_data作為validation使用，由下圖:  
![image](https://github.com/liuyihung/NCHU_CS_CH_hw0/blob/main/deep_learning/valid_train_acc.png)  
fig.1: validation set accuracy and train set accuracy in epoches  
從圖片中，我們觀察到在訓練初期validation set的accuracy 激烈震盪，但當 training set的accuracy進入平原期後，則 
![image](https://github.com/liuyihung/NCHU_CS_CH_hw0/blob/main/deep_learning/valid_train_loss.png)  
fig.2: validation set loss and train set loss in epoches  
從圖片中，我們觀察到在訓練初期出現training set loss的下降和validation set loss的激烈震盪/上升，這是訓練初期的正常現象，之後則兩者皆緩慢下降進入平原期，因此在對應的區間也確實進入learning rate下降的過程，避免over fit的情況
