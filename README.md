# airbus ship detection
This is an attempt to submit to the Kaggle Challenge for Airbus to detect ships. 

The details and data can be found at https://www.kaggle.com/c/airbus-ship-detection

Approach to the problem : 
1) First time used RLE encoding and decoding - I previously only worked with masks images 
2) Encoded connected regions as separated masks
3) RLE Function : 1 - mask, 0 - background
4) Take the individual ship masks and create a single mask array for all ships
5) Check if the the encoding - decoding is working 
6) Split into train and validation data : stratify by the number of ships appearing to have nice balances in each set
7) Undersample the empty images to get a balanced dataset 
8) Use data augmentation with various transformations 
9) Build UNET model with simple upsampling - (convoultion upsampling gave worse results) 
10) Used model with and without dropout and l1 & l2 regualarization - regularization gave worse results - dropout helped the model learn better 
11) Used dice loss and IOU loss - dice produced better results 
12) Used learning rate annealing and early stopping to make sure the model learns efficiently 
13) Saved the best weights model to use it for prediction  
14) Predicted loss for validation and test data - have not put up the images here



Things that could have been tried out with more time and resources: 

1) Different loss functions - used just DICE loss and IOU loss here  
2) Other architectures - stuck to UNET here -can possibly RESNETS and also deeper UNETS
3) Ensamble modelling - key to win kaggle challenges 
4) Using Pretrained models 
5) Stuck to Adam as optimiser - personally I would go with SGD with momentum 
6) Different activation function (used ReLU - can try ELU)
7) Different weight initialization 
8) Different batch size and epochs 




