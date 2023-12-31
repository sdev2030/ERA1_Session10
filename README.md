# ERA1_Session10
## Assignment
    1. Write a ResNet architecture for CIFAR10 that has the following architecture: 
        1. PrepLayer - Conv 3x3 s1, p1) >> BN >> RELU [64k] 
        2. Layer1 - 
            1. X = Conv 3x3 (s1, p1) >> MaxPool2D >> BN >> RELU [128k] 
            2. R1 = ResBlock( (Conv-BN-ReLU-Conv-BN-ReLU))(X) [128k]  
            3. Add(X, R1) 
        3. Layer 2 - 
            1. Conv 3x3 [256k] 
            2. MaxPooling2D 
            3. BN 
            4. ReLU 
        4. Layer 3 - 
            1. X = Conv 3x3 (s1, p1) >> MaxPool2D >> BN >> RELU [512k] 
            2. R2 = ResBlock( (Conv-BN-ReLU-Conv-BN-ReLU))(X) [512k] 
            3. Add(X, R2) 
        5. MaxPooling with Kernel Size 4 
        6. FC Layer
        7. SoftMax 
    2. Uses One Cycle Policy such that: 
        1. Total Epochs = 24 
        2. Max at Epoch = 5 
        3. LRMIN = FIND 
        4. LRMAX = FIND 
        5. NO Annihilation 
    3. Uses this transform -RandomCrop 32, 32 (after padding of 4) >> FlipLR >> Followed by CutOut(8, 8) 
    4. Batch size = 512 
    5. Use ADAM, and CrossEntropyLoss 
    6. Target Accuracy: 90% 

## Solution - Notebook [s10_assignment](https://github.com/sdev2030/ERA1_Session10/blob/main/s10_assignment.ipynb)
In this we will use above given CNN architecture to achieve target test accuracy of more than 90% from the 19th epoch.

Following are the model parameter, train and test accuracies achieved in training the model for 24 epochs.
- Model Parameters - 6,573,130
- Train Accuracy - 98.60%
- Test Accuracy - 93.07%


### Graph showing LR finder to determine the optimum learning rate to use in one cycle LR policy.
![LR finder Graph](https://github.com/sdev2030/ERA1_Session10/blob/main/images/lr_finder_graph.png)


### Graphs from training showing loss and accuracy for train and test datasets
![Training Graphs](https://github.com/sdev2030/ERA1_Session10/blob/main/images/training_graphs.png)


### Graph showing one cycle learning-rate(LR) changes during training 
![One Cycle LR](https://github.com/sdev2030/ERA1_Session10/blob/main/images/onecycle_lr.png)


### Ten misclassified images from the trained model.
![Misclassied images](https://github.com/sdev2030/ERA1_Session10/blob/main/images/wrong_classified.png)
