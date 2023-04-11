# COVID-19 detection with Chest-X-Ray using PyTorch and Flutter implementation

## Introduction
Nowadays, we are living in the COVID-19 pandemic, atypical COVID-19 infection case will damage the walls and linings of the air sacs in human lungs. As the human bodytries to fight it, the lungs become more inflamed and fill withfluid. In many cases, it is possible to perform imaging teststo support the diagnosis, determine the severity of the diseaseand assess therapeutic response. In this way, chest X-ray isusually the first imaging test in patients with suspected or confirmed COVID-19 because of its usefulness,  availability and low cost. As visual artificial learners we will generate a tool to support health professionals in the diagnosis of COVID-19 employing chest X-ray imaging tests.
There must be a high aplicability in the project and an app where it is connnected to the trained neural network and where a user can upload a X-Ray image of the lungs and get a prediction will be implemented. This will be developed in a Flutter framwork on the Dart programming language.

## Background
In order to setup a neural network adaptable to this project the Resnet networks are the most situable ones. With a 4 class data-set we chose the Resnet18 network. 

## Data Acquisition and Pre-processing
The dataset was obtained from [Kaggle](https://www.kaggle.com/tawsifurrahman/covid19-radiography-database). [6][7]

For the implementation of this project, the following 4-class dataset was used. A test set with 30 images of each class was set aside, in addition to a train set with 21045  images. Subsequently, a contrast stretch was performed for all images before training the model, this in order to obtain a better visualization of features in images with low contrast.


### Transfer Learning and Model Training
Once the data acquisition and preprocessing stage was carried out, several transformations were applied to the dataset, such as a Resize, a RandomHorizontalFlip and a  normalization. This was done using Pytorch dependencies. Subsequently, based on a transfer learning model, a ResNet18 neural network was implemented starting from a pre-trained model within Pytorch dependencies. By evaluating the predictions made by the model during the training, this process was continued until an accuracy of _0.95_ was obtained.

### Model Compiling for Mobile Implementation
Once we have trained the  model, our next step will be toobtain a Torch Script capable of being loaded and used to makeinferences, either in a desktop Python environment or in a mobile environment with Dart and Flutter frameworks as is being done in the present project.

## Results
The results file can be seen at: 

[2. evaluation_metrics.ipynb](https://github.com/ChristianConchari/COVID-19-detection-with-Chest-X-Ray-using-PyTorch/blob/master/2.%20evaluation_metrics.ipynb)

In order to evaluate the project some  metrics  must  be obtained, these will be the most important feedback to the project and may be applied to the training or data augmentation part. In order to obtain the required metrics a data extraction must be made, the model on __.pt__ and __.pth__ format will be loaded and the important characteristics will be extracted from it. The relevant metrics for a ResNet-18 neural network are:
<table>
<tr>
<th></th>
<th>ResNet-18</th>
</tr>
<tr>
<td>

|__Pathology__|
|:-|
|Normal|
|Lung Opacity|
|Viral Pneumonia|
|COVID-19|
||
|Accuracy|
|Macro avg|
|Weighted avg
</td>
<td style="text-align: center;">

|Precision|Recall|F1-Score|Support|
|-:|-:|-:|-:|
|0.91|0.77|0.83|26|
|0.89|0.1.00|0.94|33|
|1.00|0.78|0.88|36|
|0.70|0.92|0.79|25|
|||||
|||0.86|120|
|0.87|0.85|0.85|120|
|0.88|0.86|0.85|120|

</td>

</tr>
<tr>
<td>

|TL;DR|
|:-|
|Train set|
|Test set|

</td>
<td>

|Total Correct Predictions|Total Accuracy|
|-:|-:|
|21045|86.49%|
|105|__83.33%__|

</td>

</tr>
<tr>
<td>Confusion Matrix</td>
<td>

![vgg_confmat](./Result_images/Test_confussion.png)

</td>

</tr>
</table>

- __Flutter App Implementation__

A mobile interface has been created using the Flutter framework, for this purpose we made use of the pytorch mobile library, which allows us to work loading the Pytorch script  generated with the information of the trained model, to make inferences taking as input images entered by the user and giving as output the corresponding classification label.
<p align="center">
  <img  src="https://github.com/ChristianConchari/COVID-19-detection-with-Chest-X-Ray-using-PyTorch/blob/master/Result_images/app_results.png">
</p>
This figure shows a gradient prediction of the model


## Conclussions
In this project we have presented an implementation of a Convolutional Neural Network (CNN) model generated with Transfer Learning techniques, modifying the pre-trained ResNet18  network to classify chest X-ray images into four classes: normal lungs,  lungs infected with COVID-19, with viral pneumonia and pulmonary opacity. The current scenery in which  we find ourselves requires us to contribute through new solutions, in our case applying artificial intelligence to support the medical diagnosis of respiratory diseases such as COVID-19.
