# MegaPose v1: A Large-Scale Multi-View Sports Video Dataset for 3D Human Pose Estimation
We present our ongoing effort of constructing a large-scale multi-view sports video dataset for 3D human pose estimation, named MegaPose.

![](images/profile.png)

## News
* MegaPose V1 will be released soon.

## Introduction
The goal of our MegaPose dataset is to introduce a new challenging and large-scale benchmark with high-quality GT to the community of sports intelligence analysis and the community of 3D HPE. MegaPose aims to include diverse and high-quality multi-view video data, which are collected from indoor and outdoor scenarios, as well as single and multi-person scenarios of various sports. In addition, part of the data is collected from some challenging scenarios such as fast movement, special poses, heavy occlusions, varied clothing, and closely interacting motions. MegaPose is a professional sports video dataset, because all players are professional athletes. MegaPose is constructed continuously and in stages. At present, we have completed the construction of the first version, MegaPose v1, which was captured indoors from 9 kinds of sports.

|Sports category	|Single person (clips)	|Multi-person	(clips)|Subtotal	(clips)|Total number of frames|
|---|---|---|---|---|
|Rhythmic Gymnastics	|37	|0	|37	|1,095,204|
|Football  |17	|9	|26	|1,142,484|
|Basketball	|8	|19	|27	|649,812|
|Martial Arts	|24	|3	|27	|1,096,068|
|Aerobic Gymnastics	|20	|0	|20	|687,588|
|Dance Sport	|12	|15	|27	|438,648|
|Taekwondo	|0	|47	|47	|391,428|
|Sanda	|7	|2	|9	|613,836|
|Badminton	|6	|2	|8	|1,149,912|
|Total	|131	|97	|228	|7,264,980|

## Additional Experiments
### A1. Multi-View & Multi-Person (MVMP) Methods
#### A1.1 Experiments on The 12-View Data and Using Part of MegaPose v1 Data for Training
  In MegaPose v1, we have evaluated four Multi-View & Multi-Person (MVMP) methods on the 12-view data including MVPose [8], VoxelPose [40], Plane Sweep Stereo based method (PSS) [27], and Part-Aware Measurement based method (PAM) [7]. 
  
  In previous evaluation, we directly used the source code of MVPose for evaluation. For PAM method, we adopted the parameters of its source code on shelf dataset. For VoxelPose and PSS methods, we used the training strategies provided by their source codes on shelf and campus datasets, that is, we used independent 3D poses in Panoptic datasets to train 3D model in our scene. We used the parameters of VoxelPose and PSS set in the shelf dataset, and modify the space center in VoxelPose and pose depth in PSS according to our scene attributes for training and test. PAM, VoxelPose and PSS methods use the same 2D HPE result, which is the detection result of Yolov3+HRNet used in PAM.  
  
  It can be seen that we did not use the GT of MegaPose v1 for training in previous evaluation. Among four MVMP methods, VoxelPose and PSS are two methods that need to be trained. In this additional experiment, we use 3D poses of MegaPose v1 to train 3D model of VoxelPose and PSS methods. MegaPose v1 dataset consists of 97 multi-person video clips belonging to 7 different sports. For each sports, we select one video clip for training. Therefore, the MegaPose v1 training set contains 7 video clips, and have 6532 frames in single view and 78384 frames in 12 views. The remaining 90 video clips are used as the test set. 
  
  Table 7 lists the PCP scores and Table 8 lists the MPJPE scores of PSS and VoxelPose methods on the MegaPose v1 test set after they are trained by MegaPose v1 training set. In these two tables, we also compare the results of PSS and VoxelPose methods using different training sets, which are Panoptic and MegaPose v1 training set, respectively. After PSS and VoxelPose methods are trained by MegaPose v1 training set, their performance has been improved. The average PCP score of PSS method is increased from 95.56 to 96.02. The average MPJPE score of PSS method is decreased from 32.80 to 28.68. The average PCP score of VoxelPose method is increased from 91.94 to 97.13. The average MPJPE score of 23.97 method is decreased from 31.53 to 23.97. Obviously, the performance of VoxelPose method has been significantly improved after it is trained by the MegaPose v1 training set.

Table 7. PCP scores of PSS and VoxelPose methods on the MegaPose v1 test set after they are trained by MegaPose v1 training set.
|Method|Training set|Badminton|Basketball|Football|Martial Arts|Dance Sport|Sanda|Taekwondo|Average|
|---|---|---|---|---|---|---|---|---|---|
|PSS|Panoptic|98.90|95.43|96.43|96.57|91.52|95.32|94.77|95.56| 
|PSS|MegaPose v1 training set|99.05|95.81|96.98|96.60|93.44|95.77|94.52|96.02| 
|VoxelPose|Panoptic|93.93|93.02|91.04|94.48|85.98|90.13|95.03|91.94| 
|VoxelPose|MegaPose v1 training set|99.08|97.29|97.01|98.86|92.21|96.75|98.70|97.13| 

Table 8. MPJPE (mm) scores of PSS and VoxelPose methods on the MegaPose v1 test set after they are trained by MegaPose v1 training set.
|Method|Training set|Badminton|Basketball|Football|Martial Arts|Dance Sport|Sanda|Taekwondo|Average|
|---|---|---|---|---|---|---|---|---|---|
|PSS|Panoptic|24.73|30.70|28.54|37.29|44.71|32.17|31.48|32.80| 
|PSS|MegaPose v1 training set|22.59|27.45|25.62|31.79|37.19|27.95|28.20|28.68|  
|VoxelPose|Panoptic|26.48|29.87|28.99|30.65|47.95|30.36|26.42|31.53| 
|VoxelPose|MegaPose v1 training set|20.55|22.65|22.53|23.14|34.62|22.91|21.38|23.97| 

#### A1.2 Experiments on The 8-View MegaPose v1 Test Set
In this subsection, we test the performance of PAM, PSS, VoxelPose methods on the 8-view MegaPose v1 test set. In the 12-view MegaPose v1 test set presented in subsection A1.1, we select 8-view data for test, which contains 90 8-view video clips. For the methods of PSS and VoxelPose, we use their models trained in subsection A1.1, which are trained in 12-view MegaPose v1 training set. Table 9 lists the PCP scores of PAM, PSS and VoxelPose methods on the 8-view MegaPose v1 test set. Table 10 lists the MPJPE scores of PAM, PSS and VoxelPose methods on the 8-view MegaPose v1 test set. It can be seen that the performance of these three methods on 8-view MegaPose v1 test set is slightly worse than that on 12-view MegaPose v1 test set.

Table 9. PCP scores of PAM, PSS and VoxelPose methods on the 8-view MegaPose v1 test set.
|Method|Badminton|Basketball|Football|Martial Arts|Dance Sport|Sanda|Taekwondo|Average|
|---|---|---|---|---|---|---|---|---|
|PAM|97.46|92.89|95.72|94.42|90.65|91.23|94.59|93.85|  
|PSS|98.63|94.11|96.51|95.31|90.89|94.02|94.26|94.82| 
|VoxelPose|98.76|95.28|96.08|97.17|89.61|94.49|97.39|95.54| 

Table 10. MPJPE (mm) scores of PAM, PSS and VoxelPose methods on the 8-view MegaPose v1 test set.
|Method|Badminton|Basketball|Football|Martial Arts|Dance Sport|Sanda|Taekwondo|Average|
|---|---|---|---|---|---|---|---|---|
|PAM|27.60|30.66|28.86|29.91|34.04|31.02|27.71|29.97|  
|PSS|24.36|30.79|27.31|33.51|40.72|29.69|28.84|30.75| 
|VoxelPose|21.85|26.29|25.44|26.13|36.57|25.89|23.95|26.59| 


### A2 Single-View & Single-Person (SVSP) Methods
#### A2.1 Experiments on The SVSP Data without Using Part of MegaPose v1 Data for Training

In this subsection, we evaluate several SOTA SVSP methods on the MegaPose v1 including Relative Information Encoding based method (Pose3D-RIE) [50], PoseAug [51], Anatomy-aware 3D HPE method (Anatomy3D) [52], and Semantic Graph Convolutional Networks based method (SegGCN) [53]. All of them were proposed recently, and their codes are publicly available. 

In MegaPose v1, 8 kinds of sports have single-person data, and there are 131 single-person video clips. We direct use their source code to conduct experiments without using part of MegaPose v1 data for training. That is, four SVSP methods are evaluated on all SVSP data in MegaPose v1.  Table 11 lists MPJPE scores of four SVSP methods on the MegaPose v1 SVSP data and Human3.6 dataset. It can be seen that on the MegaPose v1 SVSP data, the MPJPE scores of four SVSP methods are obviously larger than that on Human3.6M dataset. 

Table 11. MPJPE (mm) scores of four SVSP methods on the MegaPose v1 SVSP data and Human3.6 dataset.
|Method|Badminton|Basketball|Football|Martial Arts|Dance Sport|Sanda|Aerobic Gymnastics|Rhythmic Gymnastics|Average|Human3.6M|
|---|---|---|---|---|---|---|---|---|---|---|
|[Pose3D-RIE](https://github.com/paTRICK-swk/Pose3D-RIE)|164.96|270.07|261.02|209.50|177.24|183.28|213.91|202.71|210.34|30.1|
|[PoseAug](https://github.com/jfzhang95/PoseAug)|168.12|227.34|237.89|212.09|177.69|164.43|220.27|197.11|200.63|38.2|
|[Anatomy3D](https://github.com/sunnychencool/Anatomy3D)|180.58|271.13|273.18|218.63|190.78|183.30|222.09|211.41|218.89|44.1|
|[SemGCN](https://github.com/garyzhao/SemGCN)|208.86|261.69|282.61|260.36|210.97|206.31|259.38|244.89|241.88|43.8|

### Reference

[7] H. Chu, J. Lee, Y. Lee, C. Hsu, J. Li, and C. Chen. Part-aware measurement for robust multi-view multi-human 3d pose estimation and tracking. In CVPR, pages 1472–1481, 2021. 7

[8] J. Dong, W. Jiang, Q. Huang, H. Bao, and X. Zhou. Fast and robust multi-person 3d pose estimation from multiple views. In CVPR, pages 7792–7801, 2019. 7

[19] K. Iskakov, E. Burkov, V. S. Lempitsky, and Y. Malkov. Learnable triangulation of human pose. In ICCV, pages 7717–7726, 2019. 7, 8

[27] J Lin and G. H. Lee. Multi-view multi-person 3d pose estimation with plane sweep stereo. In CVPR, pages 11886– 11895, 2021. 7

[35] H. Qiu, C. Wang, J. Wang, N. Wang, and W. Zeng. Cross view fusion for 3d human pose estimation. In ICCV, pages 4341–4350, 2019. 7, 8

[40] H. Tu, C. Wang, and W. Zeng. Voxelpose: Towards multi-camera 3d human pose estimation in wild environment. In ECCV, pages 197–212, 2020. 7

[46] Z. Zhang, C. Wang, W. Qiu, W. Qin, and W. Zeng. Adafuse: Adaptive multiview fusion for accurate human pose estimation in the wild. IJCV, 129(3):703–718, 2021. 2, 3, 7, 8

[50] W.K. Shan, H.P. Lu, S.S. Wang, X.F. Zhang, W. Gao. Improving robustness and accuracy via relative information encoding in 3D human pose estimation. In ACM MM, 2021. https://doi.org/10.1145/3474085.3475504. 

[51] K. H. Gong, J. F. Zhang, J. S. Feng. PoseAug: A differentiable pose augmentation framework for 3D human pose estimation. In CVPR, pages 8571-8580, 2021. 

[52] T. L. Chen, C. Fang, X.H. Shen, Y.H. Zhu, Z.L. Chen, J. B. Luo. Anatomy-aware 3D human pose estimation with bone-based pose decomposition. In TCSVT, DOI: 10.1109/TCSVT.2021.3057267, 2022. 

[53] L. Zhao, X. Peng, Y. Tian, M. Kapadia, D. N. Metaxas. Semantic graph convolutional networks for 3D human pose regression. In CVPR, pages 3420-3430, 2019.


## Datasetlink
Temporarily not unavailable, comming soon:+1: <br/>
[Rhythmic gymnastics](datasets/RhythmicGymnastics), [Football](datasets/Football), [Basketball](datasets/Basketball), [Martial Art](datasets/MartialArt), [Aerobic gymnastics](datasets/AerobicGymnastics), [Dancesport](datasets/Dancesport), [Taekwondo](datasets/Taekwondo), [Sanda](datasets/Sanda), [Badminton](datasets/Badminton)
