# 3D spacecraft component segmentation dataset
This project proposes a multi-source 3D component segmentation dataset for non-cooperative spacecraft.  
Partial of our dataset containing spacecraft downloaded from [NASA](https://nasa3d.arc.nasa.gov/) can be downloaded [here](https://drive.google.com/drive/folders/1cTScfdNdbvzIFpNxnpXc_x1ujE2V5yLr)

## Where to gain 3D spacecraft models?
 We download the CAD model of the published spacecraft from open-source websites, such as NASA (https://www.nasa.gov/, accessed on 15 March 2022), Free3d (https://free3d.com/, accessed on 15 March 2022), etc. Lately, we print the CAD models utilizing the 3D printing technology to get the 3D printed models.
![CADimage](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/CAD.pdf)
(Considering the expensive cost of the 3D printing technology, we only print a trivial number of spacecraft CAD models)

## How to gain 3D point clouds?
Simulated point clouds and actual point clouds are obtained. There are three methods to gain 3D point clouds: generating 3D point clouds via AirSim, generating 3D point clouds via SFM, generating 3D point clouds via 3D scanning of spacecraft models. 

 ### Generation of 3D point cloud via simulation engine
[AirSim](https://microsoft.github.io/AirSim/) is an open-source and cross-platform simulation engine which can imitate the lidar data for multiple different channels. In experiments, lidars of 32 channels are configured on the simulation engine, ![CADimage](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/airsim.pdf).

 ### Generation of 3D point cloud via VisualSFM
[VisualSFM](https://ccwu.me/vsfm), accessed on 15 March 2022) is a GUI application for 3D reconstruction using 2D images. VisualSFM is able to run very fast by exploiting multicore parallelism in feature detection, feature matching, and bundle adjustment. There are two methods to gain image sequences: Blender simulation, or using the camera on the Nvidia Jetson TX2. 
[Blender2.8.2](https://www.blender.org/) is used to gain the simulation image sequence of spacecraft. As shown in ![blender](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/blender.pdf), the CAD model of the Aqua satellite is imported into Blender, and a circle with a radius of 10m at 10m above the CAD model is drawn. Setting the camera's light center aligned with the model, and 600 simulation images with the size of 1024×1024 are obtained by shooting around along the circular trajectory. Lately, the simulated vision point clouds are obtained via VisualSFM and the noises within it are manually removed, thus to get the relatively clean point clouds.
The acquisition of actual image sequences uses the camera on the [Nvidia Jetson TX2 developer component](https://developer.nvidia.com/embedded/jetson-tx2). 


 ### Generation of 3D point clouds via 3D scanner
The scanner selected in this experiment is [EinScan Pro 2X Plus Handheld 3D scanner](https://www.einscan.com/handheld-3d-scanner/2x-plus/), According to the different materials of spacecraft, the scanning mode includes handheld fine scanning and handheld fast scanning. The handheld fine scanning mode is used to scan high reflective objects by pasting control points on the target, while the handheld fast scanning mode which does not need to paste control points is feasible for scanning general materials. 

## How to anno point clouds?
our annotation system is based on open-source software [CloudCompare](https://www.cloudcompare.org/),As shown in ![anno system](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/anno.png)

## Results
Part of our labeled pointclouds are list as follows
|Folder|Content|
|:---|:---|
|fbx_data|CAD models with .fbx formate downloaded from NASA|
|obj_data|CAD models with .obj formate generated from fbx_data|
|raw_point_cloud|point clouds generated from obj_data|
|labeled_point_cloud|point clouds with semantic labels|

label, number, and points of components.
|Components|Label|Points num per component|
|:---|:---|:---|
|Body|0|6500-15000|
|Panel|1|8000-12000|
|Antenna|2|300-1500|
|Others|3|6000-8000|
Attention: all point clouds are sampled into 2w points.

## Partial of our dataset can be downloaded [here](https://drive.google.com/drive/folders/1cTScfdNdbvzIFpNxnpXc_x1ujE2V5yLr).  
The dataset   
1、20000_ply_data： contains point clouds in ply format, with 20000 points per point clouds.  
2、20000txt_sampled： contains labeled point clouds in txt format, with 20000 points per point clouds, and sampled to 17500、15000、12500、10000 、7500、5000.  
3、2500txt_sampled： mini labeled dataset, with 2500 points per point clouds.  


