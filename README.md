# Capstone
Purdue University Chem Capstone Project

## 1. Label Generator

### 1.1 Libraries

|Name|Application|Note|
|-|-|-|
|tkinter|Graphical User Interface(GUI)||
|qrcode|String --> QRcode(PNG)||
|barcode|String --> Barcode(SVG)||
|re|Check input validation|Pending|
|os|File path||

### 1.2 Barcode Generating Function

Barcode generating function is for generating the label of single sample. Information for one sample is limited, we are able to generate label with the same information as the initial status without doing anyother treatment.

</br>

There's a problem we need to be aware of. Barcode have various of different type, each type of barcode have its [unique format requirment](https://www.premierelectronics.com/blog/barcode-types-identificaton-understanding)(Click hyperlink to see more information). The most commonly used format is 'EAN13'. However, it's only compatible with numbers. In our project, we need our system to be compatible with both letters and numbers and we found Code39 worked. Once we applied Code39 as our barcode format, another issue occured. 'qrcode' library can only create a SVG format file. We might need to convert SVG format into PNG format.

</br>

The figure below, is an example of the generation of barcode.

<p align="center">
  <img width="300" height="200" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/BarcodeExample.png?raw=true">
  <img width="200" height="60" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/Barcode.png?raw=true">
</p>
<p align="center">
  Figure1.Barcode Example
</p>

### 1.3 QRcode Generating Function

QRcode generating function is typically for label generation of a serie of samples. Normally, a series of information consist large amount of repeated information. If we transfer all the information into a QRcode, the graph will be in a messy. Thus, a compress algorithm is applied before 


<p align="center">
  <img width="300" height="200" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/QRcodeExample.png?raw=true">
  <img width="80" height="80" src="https://github.com/DanielZhuGY/Capstone/blob/main/images/QRcode.png?raw=true">
</p>
<p align="center">
  Figure2.QRcode Example
</p>

## 2. Dashboard for upstream process

A dashboard for biopharmaceutical upstream process is designed which includes 3 main pages. This dashboard enable researchers to observe and compare the trend for each parameter for different samples from different bioreactors within a same graph.
|Page|Usage|
|-|-|
|Dashboard|Enable researchers to observe and conduct comparison the trend for each parameter for different samples from different bioreactors within a same graph.|
|Analysis|Illustrate the correlation coefficient heatmap between each two parameters.|


## 3. Classifer

If a new sample is sent to the laboratory. Researchers need to do a DOE research to find out the best condition for cells to produce the most product we want (Highest Titer). This process is always costly and time-consuming. Thus, we developed a Big Data Management tool to help researchers to look up the history experiments. Through comparing the data, they might be able to find out some old samples which have close behaviours. In this case, they can use the old samples' parameters as a reference and this can reduce the the number of experiments.

Two kinds of classifer are developed in this capstone project. The first one is based on PCA(Principal Component Analysis) and Logistics Regression, the second one is based on CNN(Convolutional Neural Network).

### First Approach (PCA & Logistic Regression)

PCA is a method to do dimensionality reduction and try to maintain as much information as possible.

<p align="center">
 <img width="500" height="200" src="http://www.nlpca.org/fig_pca_principal_component_analysis.png">
</p>

[Source](https://www.analyticsvidhya.com/blog/2016/03/pca-practical-guide-principal-component-analysis-python/)

The path of the code is Capstone/Classifier/pca&lr.py

### Second Approach (CNN)



