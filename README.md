# Diabetic-Retinopathy-Detection
Detection of the disease from the data that contains area and perimeter of blood vessel, exudates and micro-aneurysm.<br/><hr/>


A python project that takes a csv file that contains the features such as blood vessel, exudates and microaneurysm from the retinal images and predicts the presence of 
**Diabetic Retinopathy**

## Diabetic Retinopathy
It is a condition in which due to diabetes, a patients can lose his or her eyesight. The symptoms of DR include contraction or expansion of the blood vessels, formation of yellow spot(exudates) or red small dots(micro-aneurysm) or lumps of blood(hemmprhage) in the eye, due to leakage of fluids or blood from the vessel. These can be visible in the  retinal images of the patient.


## Database
The csv file was obtained after applying various Image Processing steps to the **DIARETDB0** and **DIARETDB1** retinal images. <br/><br/>
The retinal images were in png formats. The MATLAB program takes in the images as input and calculates the area and perimeter of the features. 

Hence, the csv file contains the following columns: \
  1.Area of Blood Vessel, \
  2.Perimeter of Blood Vessel,\
  3.Area of Exudates,\
  4.Perimeter of Exudate,\
  5.Area of Micro-aneurysm,\
  6.Perimeter of Micro-aneurysm,\
  7.Probablitity of DR(0 or 1). 
  
The target variable of the dataset is a binary variable which shows 1 for the presence of DR and 0 for the absence of DR.

## Image Processing

Image processing was done by using MATLAB.
The few of the preprocessing steps applied to the image files are:\
  1.Green Scale Conversion,\
  2.Contarst Limited Adaptive Histogram Equalization(CLAHE),\
  3.Morphological Opening and Closing,\
  4.Thresholding,\
  5.Binarization,\
  6.Column Filtering.
  
The csv, thus obtained is also uploaded.


## Machine learning 

1.The csv is read using the function `read_csv()` in `pandas` library of python. \
2.The dataset is divided into predictor and target columns i.e *x* and *y*. \
3.Since the dataset was generated by the above MATLAB program, the dataset has no NA values. \
4.The values of the predictor variables have different ranges for different column. For example the area of blood vessel variable ranges from 7508 to 31872 whereas the \
  perimeter of micro-aneurysm ranges from 0 to 324.12 . The ranges were found using the `describe()` method of the pandas library. \
  To reduce the dependency of the target variable on a single predictor variable the dataset is normalized using the **z-score method**. 
  
  ##### Z-Score method: 
    The columns are normalized using- 
                x(new)=  ( x(old)- (mean of col x)) / (standard deviation of col x). 
      
5.When the **Decision Tree Classifier** was used to the accuracy of the model calculated after getting mean of the cross validation score on 5 groups of data was **0.749 or 74.9%**\
6.When **Random Forest Classifier** was used on the dataset: \
  6.1 To find the optimum n_estimators required for the model, the model was created for the n_estimators taking the range of 50 to 1000 with an interval of 50 i.e \
      [50,100,150,...1000]. \
  6.2 A plot was plotted using the `seaborn` library which had mean accuracy of the cross validation score on its y-axis and the n_estimators on its x-axis. 
  6.3 The plot showed the value of n_estimators that gave the highest accuracy. \
   
  Thus, Random Forrest Classifier gave an accuracy of **0.867 or 86.7%** with the value of n_estimators or trees in the forest as **150**. \
