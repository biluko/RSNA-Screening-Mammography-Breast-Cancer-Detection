# RSNA-Screening-Mammography-Breast-Cancer-Detection
本次比赛的目标是识别乳腺癌,使用从常规筛查中获得的筛查乳腺 X 线照片来训练模型.

## 所用算法
1. 该竞赛为一个样本标签分布极不平衡的医学影像二分类竞赛，竞赛优胜关键在于图像数据的预处理与样本不平衡问题的处理。
   
2. 本方案首先针对dicom图像进行关键兴趣区域提取（ROI extract），之后删除图像多余空白部分并根据原始比例适当填充图像区域。

3. 模型训练时，将图片放缩至适当尺寸，并选用ConvNeXtV2Tiny的ImageNet预训练模型进行迁移学习。

4. 同时采用undersample（欠采样）和引入额外数据集的方法解决样本标签不平衡问题，并设置不同负样本比例得到多个泛化模型进行集成学习。

5. 最后根据原始样本分布比例设置阈值得到最终的预测结果，并根据Kaggle公榜分数与本地验证集分数选择最佳模型。

## 预训练模型
ConvNeXtV2Tiny 

## 额外数据集
https://www.kaggle.com/datasets/pourchot/ddsm-mammography-positive-case

## 代码解读

1. 训练集数据处理：RSNA-Cropped-768x1344-train-data.ipynb

2. 额外数据处理：RSNA-extra-positive-data-process.ipynb

3. 额外数据集地址：https://www.kaggle.com/datasets/pourchot/ddsm-mammography-positive-case

4. 训练：不带额外数据集：RSNA-Convnextv2-train-folds.ipynb

5. 训练：带额外数据集：RSNA-Convnextv2-train-extra-folds.ipynb

6. 推理：RSNA-Convnextv2-inference.ipynb
