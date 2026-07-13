# SAD-GS
Open-vocabulary 3D semantic Gaussian field learning relies on multi-view 2D supervision, whose semantic targets and spatial assignments are often unreliable. Across varying viewpoints, view-dependent features cause semantic identity drift, while propagated tracker masks introduce boundary leakage and identity switches. Directly optimizing against these unreliable 2D targets forces the 3D representation to absorb multi-view contradictions, leading to severe error accumulation. To resolve this limitation, we propose \textbf{SAD-GS}, a framework for learning reliable 3D semantic Gaussian fields via dynamic geo-semantic anchoring. Specifically, \textbf{Semantic Anchor Distillation (SAD)} distills per-view visual embeddings into consensus text anchors to establish a viewpoint-invariant semantic identity. Concurrently, the \textbf{Geo-Semantic Feedback Loop (GSFL)} leverages the evolving 3D field to actively filter tracker anomalies and refine spatial mask assignments via a conservative three-gate update rule. Extensive evaluations on LERF-OVS, 3D-OVS, and Mip-NeRF360 show that \textbf{SAD-GS} consistently achieves the best overall performance in both open-vocabulary localization and semantic segmentation. These comprehensive improvements validate the effectiveness and robustness of dynamic geo-semantic anchoring for reliable 3D semantic Gaussian field learning.

## Code
The installation of OpenGaussian is similar to [3D Gaussian Splatting](https://github.com/graphdeco-inria/gaussian-splatting).

Then install the dependencies:
```
conda env create --file environment.yml
conda activate gaussian_splatting

# the rasterization lib comes from DreamGaussian
cd OpenGaussian/submodules
unzip ashawkey-diff-gaussian-rasterization.zip
pip install ./ashawkey-diff-gaussian-rasterization
```


## Data preparation

All datasets can be obtained by following the official instructions or download links provided by the corresponding baseline projects:
- **LERF-OVS**: please follow the dataset preparation instructions in [LangSplat](https://github.com/minghanqin/LangSplat)
- **3D-OVS**: please follow the official release in [3D-OVS](https://github.com/kunhao-liu/3d-ovs)
- **MipNeRF360v2**: please download the data from the official [Mip-NeRF 360 page](https://jonbarron.info/mipnerf360/)

## Checkpoint
For semantic anchor construction, object-level description generation is performed with the **Qwen3-VL API** provided by [SiliconFlow](https://siliconflow.cn/)
