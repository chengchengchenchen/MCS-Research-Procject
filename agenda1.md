# Agenda 1

## dataset

**Class:** scooter?

**Annotation status:** Are they already labeled?

**Annotation format:**

1. COCO
2. bbox vs. instance masks?

**Evaluation:** mAP



## method (Stable Diffusion + ComfyUI)

Focus: the **generation** part of the project.

Current learning: Diffusion Models, ControlNet, CLIP.

Baseline pipeline (from “**Explore the Power of Synthetic Data on Few-shot Object Detection**”):
 text2img → saliency crop → CLIP filtering → copy–paste composition.

**question**: For this project, do we need to train/fine-tune a diffusion model, or can we use pre-trained Stable Diffusion only?



## paper

1. How much real data do we actually need: Analyzing object detection performance using synthetic and real data [[link](https://arxiv.org/abs/1907.07061)]

2. Explore the Power of Synthetic Data on Few-shot Object Detection [[link](https://openaccess.thecvf.com/content/CVPR2023W/GCV/html/Lin_Explore_the_Power_of_Synthetic_Data_on_Few-Shot_Object_Detection_CVPRW_2023_paper.html)]

   Text2img

3. InstaGen: Enhancing Object Detection by Training on Synthetic Dataset [[link](https://openaccess.thecvf.com/content/CVPR2024/html/Feng_InstaGen_Enhancing_Object_Detection_by_Training_on_Synthetic_Dataset_CVPR_2024_paper.html)]

   grounding head?

   a pre-trained diffusion model with an instance-grounding head so it generates images together with **bounding boxes**.

   

   **basic theory**

4. High-Resolution Image Synthesis with Latent Diffusion Models (Stable Diffusion) [[link](https://arxiv.org/abs/2112.10752)] 

5. Adding Conditional Control to Text-to-Image Diffusion Models (ControlNet) [[link](https://openaccess.thecvf.com/content/ICCV2023/html/Zhang_Adding_Conditional_Control_to_Text-to-Image_Diffusion_Models_ICCV_2023_paper.html)]



## github

**Repo:** https://github.com/chengchengchenchen/MCS-Research-Procject

Store: weekly meeting agenda; paper; literature review & research proposal; code; thesis



## next week

continue to learn diffusion model

1. Learning Transferable Visual Models From Natural Language Supervision (CLIP) [[link](https://arxiv.org/abs/2103.00020)]

2. Data Augmentation for Object Detection via Controllable Diffusion Models  [[link](https://openaccess.thecvf.com/content/WACV2024/papers/Fang_Data_Augmentation_for_Object_Detection_via_Controllable_Diffusion_Models_WACV_2024_paper.pdf)]

   Uses **controllable diffusion (ControlNet)** to generate data and **CLIP-based scoring** for post-filtering; shows gains on COCO

3. ODGEN: Domain-specific Object Detection Data Generation with Diffusion Models [[link](https://openreview.net/forum?id=kTtK65vKvD)]

   Uses detection constraints—**class lists, counts, and scales**—to **conditionally generate instance-level images**