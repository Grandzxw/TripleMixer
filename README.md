<p align="center">
  <img src="figs/tri.png" align="center" width="22.5%">
  
  <h3 align="center"><strong>[TIP 2025] TripleMixer: A Triple-Domain Mixing Model for Point Cloud Denoising under Adverse Weather</strong></h3>

  <p align="center">
      <a href="https://scholar.google.com.sg/citations?user=miv8T6MAAAAJ&hl=zh-CN" target='_blank'>Xiongwei Zhao</a><sup>1*</sup>&nbsp;&nbsp;&nbsp;
      <a href="https://scholar.google.com.sg/citations?user=OTBgvCYAAAAJ&hl=zh-CN&oi=ao" target='_blank'>Congcong Wen</a><sup>2,3*</sup>&nbsp;&nbsp;&nbsp;
      <a href="https://scholar.google.com.sg/citations?user=VWjvfjkAAAAJ&hl=zh-CN" target='_blank'>Xu Zhu</a><sup>1#</sup>&nbsp;&nbsp;&nbsp;
      <a href="" target='_blank'>Yang Wang</a><sup>1</sup>&nbsp;&nbsp;&nbsp;
      <a href="https://www.researchgate.net/profile/Haojie-Bai" target='_blank'>Haojie Bai</a><sup>1</sup>&nbsp;&nbsp;&nbsp;
      <a href="https://scholar.google.com.sg/citations?user=WMyb00gAAAAJ&hl=zh-CN&oi=ao" target='_blank'>Wenhao Dou</a><sup>1</sup>
    <br>
  <sup>1</sup>Harbin Institute of Technology&nbsp;&nbsp;&nbsp;
  <sup>2</sup>Harvard University&nbsp;&nbsp;&nbsp;
  <sup>3</sup>New York University
  </p>

</p>


<p align="center">
  <a href="https://www.arxiv.org/pdf/2408.13802" target='_blank'>
    <img src="https://img.shields.io/badge/arXiv-2009.03137-b31b1b.svg">
  </a>
  
  <a href="https://github.com/Grandzxw/TripleMixer/stargazers" target='_blank'>
    <img src="https://img.shields.io/github/stars/Grandzxw/TripleMixer.svg">
  </a>

  <a href="" target='_blank'>
    <img src="https://visitor-badge.laobi.icu/badge?page_id=Grandzxw.TripleMixer&left_color=gray&right_color=firebrick">
  </a>

</p>



## Abstract
Adverse weather conditions such as snow, fog, and rain pose significant challenges to LiDAR-based perception models by introducing noise and corrupting point cloud measurements. To address this issue, we make the following three contributions:
1. **Point cloud denoising network:** we propose **TripleMixer**, a robust and efficient point cloud denoising network that integrates spatial, frequency, and channel-wise processing through three specialized mixer modules. TripleMixer can be seamlessly deployed as a plug-and-play module within existing LiDAR perception pipelines;
2. **Large-scale adverse weather datasets:** we construct two large-scale simulated datasets, **Weather-KITTI** and **Weather-NuScenes**, covering diverse weather scenarios with dense point-wise semantic and noise annotations;
3. **LiDAR perception benchmarks:** we establish four benchmarks: **Denoising**, **Semantic Segmentation (SS)**, **Place Recognition (PR)**, and **Object Detection (OD)**. These benchmarks enable systematic evaluation of denoising generalization, transferability, and downstream impact under both simulated and real-world adverse weather conditions.


## Updates
* 09/25/2025: Our paper has been accepted by IEEE TIP! 🎉🎉
* 08/22/2025: All codes and configurations have been updated!
* 12/26/2024: The Weather-KITTI and Weather-NuScenes datasets are publicly available on the BaiduPan platform!   
  - **Weather-KITTI:** [Download link](https://pan.baidu.com/s/1lwkIWwiLvtaM2SDKfT0SCg) (code: `xxr1`)  
  - **Weather-NuScenes:** [Download link](https://pan.baidu.com/s/1Qhr4I15W5IuamLC7gZTL8g) (code: `musq`)  
* 24/08/2024: Initial release and submitted to the Journal. The dataset will be open source soon!



## Outline
- [Dataset](#dataset)
- [Denoising Network](#denoising-network)
- [LiDAR Perception Benchmarks](#liDAR-perception-benchmarks)
- [Installation](#installation)
- [Training and Evaluation](#training-and-evaluation)
- [Dataset Generation](#dataset-generation)
- [TODO List](#todo-list)
- [Citation](#citation)
- [License](#license)
- [Acknowledgements](#acknowledgements)



## Dataset

### 1) Overview

Our **Weather-KITTI** and **Weather-NuScenes** are based on the [SemanticKITTI](https://www.semantic-kitti.org/) and [nuScenes-lidarseg](https://www.nuscenes.org/) datasets, respectively. These datasets cover three common adverse weather conditions: rain, fog, and snow and retain the original LiDAR acquisition information and provide point-level semantic labels for rain, fog, and snow. The visualization results are shown below:

<p align="center"> <img src="figs/combined.png" width="50%" height="400px"> </p>

### 2) Dataset Statistics

<p align="center"> <img src="figs/frames.png" width="85%"> </p>
<p align="center"> <img src="figs/kitti_semantic.png" width="85%"> </p>


## Denoising Network
### 1) Overview

We propose **TripleMixer**, a plug-and-play point cloud denoising network that integrates spatial, frequency, and channel-wise processing through three specialized mixer layers. TripleMixer enables interpretable and robust denoising under adverse weather conditions, and can be seamlessly integrated into existing LiDAR perception pipelines to enhance their robustness. The overview of the proposed TripleMixer denoising network is shown below:

<p align="center"> <img src="figs/triplemixer.png" width="95%"> </p>

### 2) Results Visualization

<p align="center"> <img src="figs/denoise-vis.png" width="95%"> </p>


## LiDAR Perception Benchmarks
We establish a Denoising benchmark to evaluate the performance of **our denoising model** and introduce three downstream LiDAR perception benchmarks: **Semantic Segmentation (SS)**, **Place Recognition (PR)**, and **Object Detection (OD)**, to assess the generalization of state‑of‑the‑art perception models under adverse weather and the effectiveness of our denoising model as a preprocessing step. Notably, in all downstream benchmarks, our denoising model is trained in a supervised manner solely on our Weather‑KITTI and Weather‑NuScenes datasets using only point‑wise weather labels. Meanwhile, all perception models are directly tested on real‑world adverse‑weather datasets without any retraining or fine‑tuning. 

### 1) Denoising

<p align="center"> <img src="figs/kitti-denoise.png" width="95%"> </p>
<p align="center"> <img src="figs/nus-denoise.png" width="95%"> </p>


### 2) Semantic Segmentation (SS)
* Segmentation model selection: 
  - **[SphereFormer](https://arxiv.org/pdf/2303.12766), CVPR 2023.** <sup>[**`[Code]`**](https://github.com/dvlab-research/SphereFormer)</sup>,
  - **[SFPNet](https://arxiv.org/pdf/2407.11569), ECCV 2024.** <sup>[**`[Code]`**](https://github.com/Cavendish518/SFPNet)</sup>,
  - **[PointTransformerV3](https://arxiv.org/pdf/2312.10035), CVPR 2024.** <sup>[**`[Code]`**](https://github.com/Pointcept/PointTransformerV3)</sup>,

* Benchmarks Results: 
<p align="center"> <img src="figs/ss_resu.png" width="95%"> </p>



### 3) Place Recognition (PR)
* Place Recognition model selection: 
  - **[OT](https://arxiv.org/pdf/2203.03397), IROS 2022.** <sup>[**`[Code]`**](https://github.com/haomo-ai/OverlapTransformer)</sup>,
  - **[CVTNet](https://ieeexplore.ieee.org/document/10273716), TII 2023.** <sup>[**`[Code]`**](https://github.com/BIT-MJY/CVTNet)</sup>,
  - **[LPSNet](https://arxiv.org/pdf/2312.10035), ICRA 2024.** <sup>[**`[Code]`**](https://github.com/Yavinr/LPS-Net)</sup>,

* Benchmarks Results: 
<p align="center"> <img src="figs/pr_resu.png" width="95%"> </p>


### 4) Object Detection (OD)
* Detection model selection: 
  - **[TED-S](https://arxiv.org/abs/2211.11962), AAAI 2023.** <sup>[**`[Code]`**](https://github.com/hailanyi/TED)</sup>,
  - **[PG-RCNN](https://openaccess.thecvf.com/content/ICCV2023/papers/Koo_PG-RCNN_Semantic_Surface_Point_Generation_for_3D_Object_Detection_ICCV_2023_paper.pdf), ICCV 2023.** <sup>[**`[Code]`**](https://github.com/quotation2520/PG-RCNN)</sup>,
  - **[VoxT-GNN](https://www.sciencedirect.com/science/article/pii/S0306457325000962), IPM 2025.** <sup>[**`[Code]`**](https://github.com/tusifpk/VoxT-GNN)</sup>,

* Benchmarks Results: 
<p align="center"> <img src="figs/od_resu.png" width="95%"> </p>


## Installation

We use the following environment:
```
conda create -n triplemixer
conda activate triplemixer
conda install pytorch==1.11.0 torchvision==0.12.0 torchaudio==0.11.0 cudatoolkit=11.3 -c pytorch
pip install pyaml==23.12.0 tqdm==4.63.0 scipy==1.8.0 tensorboard==2.16.2
git clone https://github.com/Grandzxw/TripleMixer
cd TripleMixer
pip install -r requirements.txt
```


## Training and Evaluation

### 1) Training
To train the Wads dataset, run:
```
python launch_train.py \
--dataset snow_wads \
--path_dataset /path/to/wads/ \
--log_path ./pretrained_models/wads/ \
--config ./configs/Wads.yaml \
--gpu 2 \
--fp16
```
For other datasets, make the corresponding modifications accordingly.


### 2) Evaluation and Test
Pre-trained models can be downloaded from [Download link](https://drive.google.com/drive/folders/1ay1vbnu-q0zepzhQ8OKyYugzLVa9uSUu?usp=drive_link)

We follow the data preprocessing pipeline of **3D_OutDet** ([https://github.com/sporsho/3D_OutDet](https://github.com/sporsho/3D_OutDet)). Before evaluation, please run `./datasets/remove_duplicate.py` to remove duplicate point cloud data, and then remap the original labels of the WADS dataset to make them compatible with TripleMixer.

To evaluate the Wads dataset, run:
```
cd test
python eval_wads.py \
--path_dataset /root/WADS \
--ckpt ./logs/wads/ckpt_best.pth \
--config ./configs/Wads.yaml \
--result_folder ./result/predictions_wads \
--phase test  \
--num_workers 12
```

To test the Wads dataset IOU, run:
```
cd test
python test_iou_wads.py 
```
For other datasets, make the corresponding modifications accordingly.


## Dataset Generation
You can generate your own Adverse Weather Dataset on other LiDAR-based point cloud datasets using the code provided in the **tools directory** of this repository!


## TODO List
- [x] Initial release. 🚀
- [x] Add download links for **Weather-KITTI** and **Weather-NuScenes**.
- [x] Add Denoising Network code.
- [x] Add train and evaluation script on Adverse Weather Dataset.
- [x] Release checkpoints.
- [ ] ...


## Citation
If you find our work useful in your research, please consider citing:

```bibtex
@ARTICLE{11262787,
  author={Zhao, Xiongwei and Wen, Congcong and Zhu, Xu and Wang, Yang and Bai, Haojie and Dou, Wenhao},
  journal={IEEE Transactions on Image Processing}, 
  title={TripleMixer: A Triple-Domain Mixing Model for Point Cloud Denoising Under Adverse Weather}, 
  year={2025},
  volume={34},
  number={},
  pages={7712-7727},
  doi={10.1109/TIP.2025.3629047}}
```
or
```bibtex
@misc{zhao2024triplemixer3dpointcloud,
      title={TripleMixer: A 3D Point Cloud Denoising Model for Adverse Weather}, 
      author={Xiongwei Zhao and Congcong Wen and Yang Wang and Haojie Bai and Wenhao Dou},
      year={2024},
      eprint={2408.13802},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2408.13802}, 
}
```
or
```bibtex
@article{zhao2024triplemixer,
  title={Triplemixer: A 3d point cloud denoising model for adverse weather},
  author={Zhao, Xiongwei and Wen, Congcong and Wang, Yang and Bai, Haojie and Dou, Wenhao},
  journal={arXiv preprint arXiv:2408.13802},
  year={2024}
}
```


## License
The dataset is based on the [SemanticKITTI](https://www.semantic-kitti.org/) dataset, provided under the [Creative Commons Attribution-NonCommercial-ShareAlike 3.0 United States License (CC BY-NC-SA 3.0 US)](https://creativecommons.org/licenses/by-nc-sa/3.0/us/), and the [nuScenes-lidarseg](https://www.nuscenes.org/) dataset, provided under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/). This dataset is provided under the terms of the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).


## Acknowledgements
This work is built on many amazing research works and open-source projects, thanks a lot to all the authors for sharing! [Robo3D](https://github.com/ldkong1205/Robo3D), [LiDAR_snow_sim](https://github.com/SysCV/LiDAR_snow_sim), [LiDAR_fog_sim](https://github.com/MartinHahner/LiDAR_fog_sim), and [3DOutDet](https://sporsho.github.io/3DOutDet).
