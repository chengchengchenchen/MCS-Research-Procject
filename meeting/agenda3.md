# Agenda 3

## summary

1. generation pipeline: comyui + stable diffusion 3.5 large + Controlnet (canny, depth)

## roadmap

1. post filter & verifier

1. whole pipeline

1. flux kontext

1. literature review structure

### post filter & verifier

#### Motivation

Inspired by [1,2], I note that diffusion-generated images have high variance in quality. To achieve greater realism, I plan to apply **CLIP-score filtering** [3] to automatically drop low-quality samples.(select top-k)

##### CLIP-based Filtering

- CLIP (**Contrastive Language–Image Pretraining**) aligns images and text in a shared embedding space.

- By computing the cosine similarity between a generated image and its prompt, we can measure **semantic consistency**. Drop out low-scoring images to ensure higher prompt fidelity and realism.

  ![CLIP](..\assets\CLIP.png)

##### Verifier: Additional Quality Measures

As highlighted in [4], multiple strategies exist to assess synthetic image quality compared to original image. Since our dataset differs from ImageNet/COCO, I currently focus on two promising self-supervised approaches: **CLIP** and **DINO(Distillation with No Labels)**[5].



References: 

1. Data Augmentation for Object Detection via Controllable Diffusion Models  [(WACV 2024)](https://openaccess.thecvf.com/content/WACV2024/papers/Fang_Data_Augmentation_for_Object_Detection_via_Controllable_Diffusion_Models_WACV_2024_paper.pdf)
2. Explore the Power of Synthetic Data on Few-shot Object Detection [(CVPRW 2023)](https://openaccess.thecvf.com/content/CVPR2023W/GCV/html/Lin_Explore_the_Power_of_Synthetic_Data_on_Few-Shot_Object_Detection_CVPRW_2023_paper.html)
3. Learning Transferable Visual Models From Natural Language Supervision [(ICML 2021)](https://proceedings.mlr.press/v139/radford21a/radford21a.pdf)
4. Scaling Inference Time Compute for Diffusion Models [(CVPR 2025)](https://openaccess.thecvf.com/content/CVPR2025/html/Ma_Scaling_Inference_Time_Compute_for_Diffusion_Models_CVPR_2025_paper.html)
5. DINOv2: Learning Robust Visual Features without Supervision [(TMLR 2024)](https://openreview.net/pdf?id=a68SUt6zFt)



### pipeline

![pipeline](..\assets\pipeline.png)

1. original image → edge map (Canny) / depth map

2. Edge/Depth + prompt → synthetic image 

3. synthetic image → post filter → selected image

4. selected image + original bounding boxes →  labeled synthetic image

5. labeled synthetic image for downstream task




Table1. Downstream task experiment design (By Dr. Brian Du)
   |                          | Yolo(mAP) | DETR(mAP) |
   | ------------------------ | --------- | --------- |
   | Real Data (R) (baseline) |           |           |
   | Synetic Data (S)         |           |           |
   | S + Filtering (F)        |           |           |
   | S + R                    |           |           |
   | S + F + R                |           |           |

### Flux kontext

I deployed  **Flux kontext** on ComfyUI. It handles prompt-driven style transfer and image blending well, but it doesn’t support **ControlNet** conditioning, which makes stable, repeatable composition difficult. 



May revisit it when consider output diversity...



### Literature review

title: Literature Review on Data Augmentation for Object Detection

![structure](..\assets\structure.png)

Q: Should I add a discussion of datasets in the autonomous driving domain to the literature review?

dataset focus on auto driving or object detection?

### Q

1. use COCO/PASCAL VOC. 
2. scooter dataset has 900 images. If we generate 10 images each image and drop 50%, then we get around 5000 images.
3. What "full" means in the design table
4. other question: week11 oral presentation, online or in person. haven't got any info...



gap paragraph in field in conclusion

data augmentation in auto driving: how to tackle niche data like GTA simulator 

https://arxiv.org/pdf/2508.07714
