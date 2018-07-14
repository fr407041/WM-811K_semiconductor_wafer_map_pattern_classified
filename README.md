# WM-811K_semiconductor_wafer_map_pattern_classified
<h3 id="Introduction"> Data Introduction </h3>

WM-811K is a semiconductor data sets which you can download from [Kaggle](https://www.kaggle.com/qingyi/wm811k-wafer-map) or [here](http://mirlab.org/dataSet/public/)

In semiconductor, there are many process issue and wafer map's pattern from CP Yield、WAT(Wafer Acceptance Test) and Particle can help the engineers find some clue. 

But there is a big problem that how to classified the wafer map pattern into serveral groups without manual action. There are many papers to survey this problem, and here I will show the result of applying deep learning.

Threre are 811457 images in the data but only 172950 images with manual label (totally 9 labels : 0、1、2、3、4、5、6、7、8).
<br>From 172950 images, label:8 (none pattern) occupied 85.2%. 

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

The kaggle's data owner [QINGYI](https://www.kaggle.com/qingyi/wm811k-wafer-map/) have do a great data explore and I cite one image about other 8 patterns from him/her (Sorry, I am lazy to generate again ...).

![image](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/8%20category%20pattern.png)

If we just predict all patterns are label:8 (none pattern), we will get 85.2% baseline accuracy for this data set. 
<br>It will make us easily misleading to believe we have build a great model for this problem. But in fact we may get low accuracy classified result for the remain 14.8% data.

**So first I define the problem is to seaparate 8 pattern from 25519 images (without none patterns)**

P.S There are many scholars use 172950 images to publish their papers and claim they got high accuracy, but in my view it's ... mmh ... you know.

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

For test data set, I get 92.95% accuracy. Below is my classified confusion matrix

![Confusion_Matrix](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/test%20data%20confusionMatrix.png)

![Classified_Result](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/test_data_classified_rate.png)



<h3> Conclusion and future work </h3>


