## MegaPose v1: A Large-Scale Multi-View Sports Video Dataset for 3D Human Pose Estimation
We present our ongoing effort of constructing a large-scale multi-view sports video dataset for 3D human pose estimation, named MegaPose.

![](images/profile.png)

## Introduction
The goal of our MegaPose dataset is to introduce a new challenging and large-scale benchmark with high-quality GT to the community of sports intelligence analysis and the community of 3D HPE. MegaPose aims to include diverse and high-quality multi-view video data, which are collected from indoor and outdoor scenarios, as well as single and multi-person scenarios of various sports. In addition, part of the data is collected from some challenging scenarios such as fast movement, special poses, heavy occlusions, varied clothing, and closely interacting motions. MegaPose is a professional sports video dataset, because all players are professional athletes. MegaPose is constructed continuously and in stages. At present, we have completed the construction of the first version, MegaPose v1, which was captured indoors from 9 kinds of sports.


|Sports category	|Single person (clips)	|Multi-person	(clips)|Subtotal	(clips)|Total number of frames|
|---|---|---|---|---|
|Rhythmic gymnastics	|37	|0	|37	|1,095,204|
|Football  |17	|9	|26	|1,142,484|
|Basketball	|8	|19	|27	|649,812|
|Martial Art	|24	|3	|27	|1,096,068|
|Aerobic gymnastics	|20	|0	|20	|687,588|
|Dance sport	|12	|15	|27	|438,648|
|Taekwondo	|0	|47	|47	|391,428|
|Sanda	|7	|2	|9	|613,836|
|Badminton	|6	|2	|8	|1,149,912|
|Total	|131	|97	|228	|7,264,980|

## Evaluation

The lastest three 3D human pose estimation algorithms are evaluated on MegaPose V1 with their pretrained models. The following table shows the evaluation result (MPJPE (mm)) on 8 kinds of sports, and the table also shows the three models' performance on Human3.6 dataset.

|Baseline|Rhythmic gymnastics|Football|Basketball|Martial Art|Sports Aerobics|Dance sport|Sanda|Badminton|Average|Human3.6|
|---|---|---|---|---|---|---|---|---|---|---|
|[Pose3D-RIE](https://github.com/paTRICK-swk/Pose3D-RIE)|336.57|347.57|420.45|337.13|385.92|320.32|343.69|328.97|352.58|30.1|
|[PoseAug](https://github.com/jfzhang95/PoseAug)|477.58|450.49|476.87|488.61|482.63|465.42|465.73|462.97|471.29|50.2|
|[Anatomy3D](https://github.com/sunnychencool/Anatomy3D)|358.3|367.89|433.15|369.6|398.34|350.36|359.04|361.03|374.71|44.1|


## Datasetlink
Temporarily not unavailable, comming soon:+1: <br/>
[Rhythmic gymnastics](datasets/RhythmicGymnastics), [Football](datasets/Football), [Basketball](datasets/Basketball), [Martial Art](datasets/MartialArt), [Aerobic gymnastics](datasets/AerobicGymnastics), [Dancesport](datasets/Dancesport), [Taekwondo](datasets/Taekwondo), [Sanda](datasets/Sanda), [Badminton](datasets/Badminton)
