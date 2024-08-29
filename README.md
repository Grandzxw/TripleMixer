[![arXiv](https://img.shields.io/badge/arXiv-2009.03137-b31b1b.svg)](https://www.arxiv.org/abs/2408.13802)

# TripleMixer: A 3D Point Cloud Denoising Model for Adverse Weather

This is the official repository of the **Weather-KITTI** and **Weather-NuScenes** dataset. For technical details, please refer to:

**TripleMixer: A 3D Point Cloud Denoising Model for Adverse Weather** <br />
[Xiongwei Zhao*](https://github.com/Grandzxw), [Congcong Wen*](https://scholar.google.com.sg/citations?user=OTBgvCYAAAAJ&hl=zh-CN&oi=ao), Yang Wang, 
[Haojie Bai](https://www.researchgate.net/profile/Haojie-Bai), [Wenhao Dou](https://scholar.google.com.sg/citations?user=WMyb00gAAAAJ&hl=zh-CN&oi=ao). <br />

**[[Paper](https://www.arxiv.org/abs/2408.13802)] [[Blog]()][[Download]()] ** <br />

### (1) Dataset

#### 1 Overview

In this Work, we propose our synthetic adverse weather datasets, named **Weather-KITTI** and **Weather-NuScenes**, which are based on the [SemanticKITTI](https://www.semantic-kitti.org/) and [nuScenes-lidarseg](https://www.nuscenes.org/) datasets, respectively. These datasets cover three common adverse weather conditions: rain, fog, and snow and retain the original LiDAR acquisition information and provide point-level semantic labels for rain, fog, and snow.

<p align="center"> <img src="Fig/combined.png" width="95%" height="700px"> </p>
<p align="center"> <img src="Fig/comparison.png" width="95%"> </p>


#### 2 Dataset Statistics

<p align="center"> <img src="Fig/frames.png" width="95%"> </p>

<table border="0">
  <tr>
    <td><img src="Fig/kitti_semantic.png" width="100%"></td>
    <td><img src="Fig/nus_semantic.png" width="100%"></td>
  </tr>
</table>

<table style="border: none; border-collapse: collapse;">
  <tr>
    <td style="border: none;"><img src="Fig/kitti_semantic.png" width="100%"></td>
    <td style="border: none;"><img src="Fig/nus_semantic.png" width="100%"></td>
  </tr>
</table>
