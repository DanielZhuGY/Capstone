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
