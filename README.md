# Traffic sign detection

The following project has as an objective to build a Neural Network capable of properly classify different traffic signs, for this project we will use the German Traffic Sign Recognition Benchmark available at the following link: https://sid.erda.dk/public/archives/daaeac0d7ce1152aea9b61d9f1e19370/published-archive.html.

The model was trained on google collab.

The [Jupyter Notebook](https://github.com/fedllanes/traffic/blob/master/Traffic.ipynb)

# Dataset

The dataset is divided on the training set and the testing set, with the training set containing 39209 pictures and the test set 12630 pictures, roughly a 75-25 ratio. There are also 43 different classes to which each image can belong to. 

Pictures for each one of the classes:

![Examples](readme_images/examples.png)

Histogram of the count of instances for each class:


![Histogram](readme_images/hist.png)

# Pre-processing 

The images have to be scaled to a 48x48 pixel image, and we need to roll the axis.

# Model

I use keras to build the CNN, the CNN used is the following.

![Model](readme_images/CNN.jpeg)


After trying several variations of the CNN, with different parameters, I've found this to be the one with the best accuracy on the test data.

# Results

The CNN was trained for 20 epochs, since for more than 20 epochs the model starts overfitting. We ended up with an acc of 0.9986 and a validation accuracy of 0.9976. We can see how the model starts converging after around 10 epochs. Our batch size was 32.

![Acc](readme_images/acc.png)

The accuracy on the test set is 98.33%, which is pretty good for our simple model and higher than a lot of participants on kaggle.

## Confusion matrix

![Confusion matrix](readme_images/confusion.png)

The confusion matrix shows us which were the classes that had the most trouble being properly classified. These are class 41(End of no passing), 30(Beware of ice/snow), and 21(Double curve).

## Mislabeling

Some examples of misclassified items are: 

![Mismatches](readme_images/mismatches.png)

Mismatches tend to be very low quality pictures that would be extremely hard to recognize even for a human, with some exceptions that don't appear as difficult. Also, some of the pictures appear to be particularly dark, meaning that increasing its brighteness could increase the accuracy.

# Conclusion

The results obtained were satisfactory, the accuracy wasn't bad at all on the never seen dataset, with over 98% of traffic signs being properly recognized (out of 43 classes). While this is impressive, more could be done to improve the quality of the model.

Some ideas include:

* Increasing the luminosity of the pictures using opencv.

* Detecting the contours of each traffic sign, and cropping it off, making sure they are all positioned the same way.
