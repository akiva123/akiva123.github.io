---
layout: post
title:      "Convolutional Neural Network"
date:       2021-01-28 19:11:26 +0000
permalink:  convolutional_neural_network
---


A convolutional neural network (CNN) has an input, output, and multiple hidden layers. The hidden layers have a series of convolutional layers that produce the dot product of filter weights and pixel matrices. A filter is used to dimentionally reduce an image to find high frequency parts of the image. Kernel size specifies the dimensions of the filter. An activation function determines neuron weight from one layer to the next. The convolutional layer is followed by a pooling layer, which uses a filter to reduce the dimensions of the convoluted result into fewer parameters.  The remaining layers after the flatten layer classify the image.  

model1 = keras.models.Sequential([
    keras.layers.Conv2D(64, 3, input_shape=[150, 150, 3]),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Conv2D(128, 3, activation='relu'),
    keras.layers.Conv2D(128, 3, activation='relu'),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Conv2D(256, 3, activation='relu'),
    keras.layers.Conv2D(256, 3, activation='relu'),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Flatten(),
    keras.layers.Dense(128, activation='relu',),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dense(1, activation='sigmoid'),
])

The Loss value implies how poorly the model is after each iteration of optimization. Loss increases as the predicted probability diverges from the actual label. The optimizer alters the model weights and learning rate to reduce the loss. SGD calculates which way the weights should be altered so that the function can reach a minima. Accuracy is the ratio of true occurences to true and false occurences. Precision is the ratio of true positives to all positives. Recall is the ratio of true positives to all actual true values. F1 is the harmonic mean of precision and recall.

from keras.optimizers import SGD

sgd = SGD(learning_rate=0.01)
model1.compile(loss="binary_crossentropy", optimizer=sgd, metrics=["accuracy",precision,recall,f1])

Regularization modifies the learning algorithm so that the model generalizes better. L2 and L1 regularization add a penalty term that adjusts the loss function by decreasing the weight matices, reducing model overfitting. The regularization term differs in L1 and L2. In L1 lamda is the absolute value and decreases the weights toward and possibly to zero. In L2 the penalty term, lambda, is squared and decreases the weights toward zero but not exactly zero. 

from keras.regularizers import l2

model2 = keras.models.Sequential([
    keras.layers.Conv2D(64, 3, input_shape=[150, 150, 3]),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Conv2D(128, 3, activation='relu'),
    keras.layers.Conv2D(128, 3, activation='relu'),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Conv2D(256, 3, activation='relu'),
    keras.layers.Conv2D(256, 3, activation='relu'),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Flatten(),
    keras.layers.Dense(128, activation='relu'
                       ),
    keras.layers.Dense(64, activation='relu', kernel_regularizer=l2(0.0001)
                       ),
    keras.layers.Dense(1, activation='sigmoid'),
])

Dropout is a regularization technique that randomly turns off some neurons during each iteration of training. 

model3 = keras.models.Sequential([
    keras.layers.Conv2D(64, 3, input_shape=[150, 150, 3]),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Conv2D(128, 3, activation='relu',),
    keras.layers.Conv2D(128, 3, activation='relu',),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Conv2D(256, 3, activation='relu'),
    keras.layers.Conv2D(256, 3, activation='relu'),
    keras.layers.MaxPooling2D(pool_size=2),
    keras.layers.Flatten(),
    keras.layers.Dense(128, activation='relu'),
    keras.layers.Dropout(0.5),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dropout(0.5),
    keras.layers.Dense(1, activation='sigmoid'),
])

Early stopping is a cross validation method that ends trainig once the performance on the validation set begins to decrease.

from keras.callbacks import EarlyStopping

early_stop = EarlyStopping(monitor='val_loss', min_delta=1e-08, patience=0, verbose=1,
                           mode='auto')

callbacks_list = [early_stop]

history4 = model4.fit(train_images, train_labels, epochs=10,class_weight={0: .5,1: .5}, validation_data=(val_images, val_labels)
                     ,callbacks=callbacks_list)





