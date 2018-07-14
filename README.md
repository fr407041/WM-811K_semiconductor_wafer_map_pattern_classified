# WM-811K_semiconductor_wafer_map_pattern_classified
<h3 id="Introduction"> Data Introduction </h3>

WM-811K is a semiconductor data sets which you can download from [Kaggle](https://www.kaggle.com/qingyi/wm811k-wafer-map) or [here](http://mirlab.org/dataSet/public/)

In semiconductor, there are many process issue and wafer map's pattern from CP Yield、WAT(Wafer Acceptance Test) and Particle can help the engineers find some clue. 
<br>But there is a big problem that how to classified the wafer map pattern into serveral groups without manual action. There are many papers to survey this problem, and here I will show the result of applying deep learning.

Threre are 811457 images in the data but only 172950 images with manual label.




From 172950 images, label:8 (none pattern) occupied 85.2%. 

![images](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/none_patterns.png)

The other remain pattern (14.8%) are 

0. Center:   (2.5%) 

1. Donut:    (0.3%) 

2. Edge-Loc: (3.0%)

3. Edge-Ring:(5.6%) 

4. Loc:      (2.1%)

5. Random:   (0.5%) 

6. Scratch:  (0.7%)

7. Near-full:(0.1%)

The kaggle's data owner [QINGYI](https://www.kaggle.com/qingyi/wm811k-wafer-map/) have do a great data explore and I cite one image about other 8 patterns from him/her (Sorry, I am lazy to generate again ...).

![image](https://github.com/fr407041/WM-811K_semiconductor_wafer_map_pattern_classified/blob/master/images/8%20category%20pattern.png)

If we just predict all patterns are label:8 (none pattern), we will get 85.2% baseline accuracy for this data set. 
<br>It will make us easily misleading to believe we have build a great model for this problem. But in fact we may get low accuracy classified result for the remain 14.8% data.

**So first I define the problem is to seaparate 8 pattern from 25519 images (without none patterns)**

P.S There are many scholars use 172950 images to publish their papers and claim they got high accuracy, but in my view it's ... mmh you know.

<>
