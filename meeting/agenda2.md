# Agenda 2

## summary

1. dataset: scooter https://universe.roboflow.com/kicksquad/scooter-only
2. image generation pipeline: img2img
3. object detection: YOLO/DERT (real time, fast detect)
4. git repo: https://github.com/chengchengchenchen/MCS-Research-Procject

## roadmap

1. pipeline: comyui + stable diffusion 3.5 large + Controlnet (canny, depth)
1. post filter (CLIP score)
1. literature review



### pipeline

1. environment:

   VRAM: 32GB

   diffusion model: Stable Diffusion 3.5 Large (FP8 scaled)

   controlnet: SD3.5 Large — Canny, Depth

2. **original image** → **edge map** (Canny) / **depth map**

   **Edge/Depth + prompt → synthetic image** (via SD3.5 + ControlNet)

   **synthetic image  + original bounding boxes →  labeled synthetic image**

   used latest stable diffusion 3.5 and controlnets

   *Reference:* Data Augmentation for Object Detection via Controllable Diffusion Models  [[link](https://openaccess.thecvf.com/content/WACV2024/papers/Fang_Data_Augmentation_for_Object_Detection_via_Controllable_Diffusion_Models_WACV_2024_paper.pdf)]

   ![pipeline_in_agenda2](..\assets\pipeline_in_agenda2.png)

3. Experiments Tried: 

   - Canny only:  [workflow](..\comyui\workflow\canny.json)
   - Depth only: poor results
   - Canny + Depth together: poor results

4. canny: ![canny-compare](..\assets\canny-compare.png)

   ![canny-compare2](..\assets\canny-compare2.png)

   

   depth: ![ComfyUI_00253_](..\assets\ComfyUI_00253_.png)

   canny + depth: ![ComfyUI_00195_](..\assets\ComfyUI_00195_.png)



### post filter

TODO：Add **CLIP-score filtering** to drop low-quality synthetic images.

References: 

1. Data Augmentation for Object Detection via Controllable Diffusion Models  [[link](https://openaccess.thecvf.com/content/WACV2024/papers/Fang_Data_Augmentation_for_Object_Detection_via_Controllable_Diffusion_Models_WACV_2024_paper.pdf)]
2. Explore the Power of Synthetic Data on Few-shot Object Detection [[link](https://openaccess.thecvf.com/content/CVPR2023W/GCV/html/Lin_Explore_the_Power_of_Synthetic_Data_on_Few-Shot_Object_Detection_CVPRW_2023_paper.html)]



### literature review

plan to finish within the next 2 weeks

due of research proposal and literature review is 9.21



layout to image