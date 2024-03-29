# Capstone
Purdue University ChemE Capstone Project. A big data managment tool for biopharmaceutical upstream process.

## 1. Label Generator

### Barcode Generating Function

Barcode generating function is for generating the label of single sample. Information for one sample is limited, we are able to generate label with the same information as the initial status without doing anyother treatment.

</br>
One issue we need to be aware of. Barcode have various of different type, each type of barcode have its [unique format requirment](https://www.premierelectronics.com/blog/barcode-types-identificaton-understanding)(Click hyperlink to see more information). The most commonly used format is 'EAN13'. However, it's only compatible with numbers. In our project, we need our system to be compatible with both letters and numbers and we found Code39 worked.
</br>

The figure below, is an example of the generation of barcode.

<p align="center">
  <img width="250" height="200" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/BarcodeExample.png?raw=true">
  <img width="200" height="60" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/Barcode.png?raw=true">
</p>
<p align="center">
  Figure1.Barcode Example
</p>

### QRcode Generating Function

QRcode generating function is typically for label generation of a serie of samples. Normally, a series of information consist large amount of repeated information. If we transfer all the information into a QRcode, the graph will be in a messy. Thus, a compress algorithm is applied before 


<p align="center">
  <img width="250" height="200" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/QRcodeExample.png?raw=true">
  <img width="80" height="80" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/QRcode.png?raw=true">
</p>
<p align="center">
  Figure2.QRcode Example
</p>

## 2. Dashboard for upstream process

The dashboard system is based on a library called [Dash](https://dash.plotly.com/). Two functions are embedded in the dashboard system. Dash library is a powerful 
|Page|Usage|
|-|-|
|Time series line chart|Empty samples are dropped automatically. Is able to conduct comparison between both different samples as well as different process conditions|
|Correlation coefficient heat map|Illustrate the correlation coefficient heat map between each two parameters.|</br>
<p align="center">
  <img width="500" height="300" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/linechart.png?raw=true">
  <img width="300" height="300" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/coef.png?raw=true">
</p>

## 3. Classifer

Once a new cell is sent to the laboratory, researchers need to do a huge amount of experiments to find out the best condition for the cell to maximize yield(Highest Titer). This process is always costly and time-consuming since there are a lot of variables in the upstream process. Thus, we developed a Big Data Management tool to help researchers to look up the history experiments. Through comparing the data, they are able to find out some old cells which have close behaviours. In this case, they can use the old cells' process data as a reference and  reduce the the number of experiments.

Two approaches are tried in this project. The first one is based on Principal Component Analysis and Logistics Regression, the second one is based on Convolutional Neural Network.

### PCA & Logistic Regression

PCA is a method to process dimensional reduction and maintain as much information as possible. This algorithm can reduce the number of calculation later on.

<p align="center">
 <img width="500" height="200" src="http://www.nlpca.org/fig_pca_principal_component_analysis.png">
</p>

[Picture for principal component analysis convert a 3D data into a 2D data](https://www.analyticsvidhya.com/blog/2016/03/pca-practical-guide-principal-component-analysis-python/)


Logistic Regression is one of the most popular methods in building classifier. It can be seen as a combination of a linear regression and an activation function. The output can show the probability of which class it belongs to.

Code..

### Convolutional Neural Network

One lethal drawback for the Logistic Regression is it can only conduct comparison for a specific time node(D1 VS D1). However, the data generated from upstream process is continuous, each data point in a process is not independent. One particular point can not represent the whole process. Thus, we want to make comparison among those time series line charts generated by our dashboard system. The main idea for us to apply convolutional neural network is the trend of process operator will varies across different kind of cells. The amount of data for each cells may vary as well. Since, we turned multiple nodes into a line chart and applied computer vision to identify similarity. In another words, we tried to let the computer to behave like a researcher, searching for representitive characteristics in different kinds of cell according to the dashboard we built on the previous chapter.

For the CNN model in this research, I imitate the architecture of one of the most popular architecture in CNN, the letNet-5. Some adjustments are conducted, The detail architechture of our CNN model is shown in the following table.

|Layer(type)|Output Shape|Parameter Number|
|-|-|-|
|Conv2D(Activation:ReLu)|(None,332,209,32)|11232|
|Conv2D(Activation:ReLu)|(None,328,205,32)|25632|
|MaxPooling|(None,82,51,32)|0|
|Dropout|(None,78,47,64)|0|
|Conv2D(Activation:ReLu)|(None,82,51,64)|51264|
|Conv2D(Activation:ReLu)|(None,78,47,64)|102464|
|MaxPooling|(None,39,23,64)|0|
|Dropout|(None,78,47,64)|0|
|Flatten|57408|0|
|Dense(Activation:ReLu)|512|29393408|
|Dropout|512|0|
|Dense(Activation:SoftMax)|11|0|

## 4. Result and Conclusion

One of the data sheets is used as the training set for training our model. Another data sheets is used as the test set to check the accuracy of the classifier. Here comes the result. 

For the Logistic Regression</br>
<img width="400" height="200" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/result1.png?raw=true"></br>
The accuracy is 20%

For the Convolutional Neural Network</br>

<img width="300" height="100" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/result3.png?raw=true"></br>
The accuracy is 70%

Compare with some other result in the research of convolutional neural network. 60% of accuracy is still not satisfied. One issue is the insufficient of training and testing set. Another issue is the defect of dataset such as some outliers and some missing values.

<img width="400" height="300" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/defect.png?raw=true">

## 5. Future works

1. Learn SQL and try to connect our dashboard into a SQL database.
2. Be familiar with HTML and Dash, make the interface more userfriendly.
3. Applied a algorithm to deal with those outliers as well as missing value. Use L1 instead of L2 might be a good approach to minimize the influence of those outliers.
