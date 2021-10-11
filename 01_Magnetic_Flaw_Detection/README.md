
# [Magnetic flaw detection](https://github.com/borisenko-ru/ds_projects/blob/main/01_Magnetic_Flaw_Detection/task.ipynb)

## Project description

Magnetic flaw detection measurements were made. During each measurement, three channels were recorded. Each measurement contains info about defect location: external (OD) or internal (ID). Also, defects may belong to the different types (e.g. corrosion, scratch, etc.).
245 measurements of a pipe were made in total. 100 measurements are classified with defect location (OD or ID) and represented in the dataset for modelling purposes. Other 145 measurements have hidden values of defect location and they are need to be predicted.

Tasks:
EDA (exploratory data analysis). Draw conclusions.
Supervised classification - using provided labels train model(s), predict defect location for unlabeled samples. Metrics - F1 score (weighted). Goal - score > 0.8
Unsupervised clustering: Try to split defects into types using different clustering methods. Demonstrate the most typical representative of each cluster.


## Data description

**Технологический процесс**

- id - measurement number
- time - measurement time, sec
- ch0 - channel with measurements 0
- ch1 - channel with measurements 1
- ch2 - channel with measurements 2
- Unnamed: 0 - duplicate of the **time** column

## Project structure

1. Objective
2. EDA (Exploratory Data Analysis)
3. Data Feature Engineering
4. Supervised Learning
- Decision Tree Classification
- Random Forest Classification
- Logistic Regression
- Defect location prediction to unclassified part of the data
5. Unsupervised Learning
- Clustering with classified data
- K-means Clustering
- DBSCAN Clustering
Conclusion

## Libraries
`pandas` `numpy` `seaborn` `matplotlib` `sklearn`

## Conclusion

Exploratory data analysis demonstrates that:
- Internal (ID) defects detection data has wider statistical distribution. The signal width is larger for the internal defects
- External (OD) defects detection data has leptokurtic distribution with high degree of peakedness. More than 10 times larger in comparison with ID data which is almost mesokurtic. The signal amplitude is larger for the external defects
- Channel 0 data for ID defect is moderately skewed with almost normal distribution
- Channel 0 data for OD defect has high negative skewness
- Channel 1 data for both defects locations (OD and ID) has high negative skewness. The mean and median are less than the mode. Median amplitude of measurements is higher than mean (average) amplitude through all dataset. indicating presense of extrimely low values in dataset.
- Channel 2 data for both defect locations (OD and ID) has high positive skewness. The mean and median are more than the mode. Median amplitude of measurements is lower than mean (average) amplitude indicating presense of extrimely high values in dataset.
- It was found that the kurtosis is highly different for data distribution analysis of OD and ID defects. Additional data features were generated - kurtosis for every measurement number for each of three channels.

For supervised learning by binary classification the following models were evaluated. To discover patterns and information that was previously undetected, clustering models were used in unsupervised learning.
