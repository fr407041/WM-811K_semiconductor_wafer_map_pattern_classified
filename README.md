# WM-811K_semiconductor_wafer_map_pattern_classified
<h3 id="Introduction"> Data Introduction </h3>

The WM-811K semiconductor data sets can be downloaded from [Kaggle](https://www.kaggle.com/qingyi/wm811k-wafer-map) or [here](http://mirlab.org/dataSet/public/). In the semiconductor industry, engineers rely on wafer map patterns from CP Yield, WAT (Wafer Acceptance Test), and Particle to identify process issues. However, classifying these wafer map patterns into groups without manual intervention is a major challenge. Many papers have investigated this problem, and I will present the results of using deep learning to address it.

The dataset contains 811,457 images, but only 172,950 images have manual labels, comprising a total of nine labels: 0, 1, 2, 3, 4, 5, 6, 7, and 8. Among these images, label 8 (representing no pattern) accounts for 85.2% of the total.

![images](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/none_patterns.png)

The other remain pattern (14.8%) are 

0. Center :   4294(2.5%) 

1. Donut :    555(0.3%) 

2. Edge-Loc : 5189(3.0%)

3. Edge-Ring : 9680(5.6%) 

4. Loc :      3593(2.1%)

5. Random :   866(0.5%) 

6. Scratch :  1193(0.7%)

7. Near-full : 149(0.1%)

The data owner of Kaggle, [QINGYI](https://www.kaggle.com/qingyi/wm811k-wafer-map/), has conducted an extensive data exploration and provided an image showing the other eight patterns (apologies for not generating it again). If we predict that all patterns belong to label 8, we can achieve an 85.2% baseline accuracy for this dataset. However, this may lead to a false sense of confidence in the model's performance, as we may obtain low-accuracy classification results for the remaining 14.8% of the data.

![image](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/8%20category%20pattern.png)

Therefore, our goal is to separate the eight patterns from the 25,519 images that do not belong to the none pattern category. It is worth noting that many researchers have used all 172,950 labeled images to claim high accuracy, which in our view may be misleading.

<h3> Data split </h3>

I split 25519 images into 15316(60%) train、3823(15%) validation and 6380(25%) test and use test data sets to varified my model.

**train : 15316(60%)**

0. Center :   2598(17.0%) 

1. Donut :    326(2.1%) 

2. Edge-Loc : 3081(20.1%)

3. Edge-Ring : 5873(38.3%) 

4. Loc :      2106(13.8%)

5. Random :   516(3.4%) 

6. Scratch :  719(4.7%)

7. Near-full : 97(0.6%)

**validation : 3823(15%)**

0. Center :   640(16.7%) 

1. Donut :    78(2.0%) 

2. Edge-Loc : 779(20.4%)

3. Edge-Ring : 1426(37.3%) 

4. Loc :      571(14.9%)

5. Random :   124(3.2%) 

6. Scratch :  186(4.9%)

7. Near-full : 19(0.5%)

**test : 6380(25%)**

0. Center :   1056(16.6%) 

1. Donut :    151(2.4%) 

2. Edge-Loc : 1329(20.8%)

3. Edge-Ring : 2381(37.3%) 

4. Loc :      916(14.4%)

5. Random :   226(3.5%) 

6. Scratch :  288(4.5%)

7. Near-full : 33(0.5%)

<h3> Model training progress </h3>

I train for 40 epochs and get 96.4% for train and 93.3% for validation. Below is my training history.

![Training_History](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/training_history.png)

![Training_Progress](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/training%20Progess.png)

<h3> Test data result </h3>

For the test data set, I get 92.95% accuracy (It's similar to validation's accuracy). Below is my classified confusion matrix

![Confusion_Matrix](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/test%20data%20confusionMatrix.png)

![Classified_Result](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/test_data_classified_rate.png)

You can download the [test data classified result](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/test_classified.csv) and [validate data classfied result](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/valid_classified.csv) to check.

The download file will show below information 

![detail](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/detail_classfied.png)

The prior column info are correspond to WM-811K data set.

<h3> Conclusion and future work </h3>

Due to certain reasons, I am unable to share my model at the moment. However, I have demonstrated the potential of solving the wafer map pattern classification problem in the semiconductor industry, and I am confident that I can improve the model in the future.

<br> Moving forward, there are several things that I plan to do:

1. Include the "none" (label:8) pattern in the classification, but carefully consider the proportion of this pattern in the dataset to ensure that the model is not misleading or cheating. Thus, there will be a total of nine patterns (0, 1, 2, 3, 4, 5, 6, 7, 8) for classification.

2. There are still many mislabeled instances in the dataset, which results in reduced accuracy. However, it is challenging to verify the correctness of all manual labels. Hence, I need to explore alternative approaches to address this issue.

Reference :

1. https://www.kaggle.com/qingyi/wm811k-wafer-map/discussion/57318#latest-338421
