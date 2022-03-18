# spacecraft_3D_component_segmentation_dataset
This project proposes a multi-source 3D component segmentation dataset for non-cooperative spacecraft.
## Where to gain 3D spacecraft models?
 We download the CAD model of the published spacecraft from open-source websites, such as NASA (https://www.nasa.gov/, accessed on 15 March 2022), Free3d (https://free3d.com/, accessed on 15 March 2022), etc. Lately, we print the CAD models utilizing the 3D printing technology to get the 3D printed models.
![CADimage](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/CAD.pdf)
(Considering the expensive cost of the 3D printing technology, we only print a trivial number of spacecraft CAD models)

## How to gain 3D point clouds?
Simulated point clouds and actual point clouds are obtained. There are three methods to gain 3D point clouds: generating 3D point clouds via AirSim, generating 3D point clouds via SFM, generating 3D point clouds via 3D scanning of spacecraft models. 

 ### Generation of 3D point cloud via simulation engine
![AirSim](https://microsoft.github.io/AirSim/) is an open-source and cross-platform simulation engine which can imitate the lidar data for multiple different channels. In experiments, lidars of 32 channels are configured on the simulation engine, ![CADimage](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/airsim.pdf).

 ### Generation of 3D point cloud via VisualSFM
![VisualSFM](https://ccwu.me/vsfm), accessed on 15 March 2022) is a GUI application for 3D reconstruction using 2D images. VisualSFM is able to run very fast by exploiting multicore parallelism in feature detection, feature matching, and bundle adjustment. There are two methods to gain image sequences: Blender simulation, or using the camera on the Nvidia Jetson TX2. 
![Blender2.8.2](https://www.blender.org/) is used to gain the simulation image sequence of spacecraft. As shown in ![blender](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/blender.pdf), the CAD model of the Aqua satellite is imported into Blender, and a circle with a radius of 10m at 10m above the CAD model is drawn. Setting the camera's light center aligned with the model, and 600 simulation images with the size of 1024×1024 are obtained by shooting around along the circular trajectory. Lately, the simulated vision point clouds are obtained via VisualSFM and the noises within it are manually removed, thus to get the relatively clean point clouds.
The acquisition of actual image sequences uses the camera on the ![Nvidia Jetson TX2 developer component](https://developer.nvidia.com/embedded/jetson-tx2). 


 ### Generation of 3D point clouds via 3D scanner
The scanner selected in this experiment is ![EinScan Pro 2X Plus Handheld 3D scanner](https://www.einscan.com/handheld-3d-scanner/2x-plus/), According to the different materials of spacecraft, the scanning mode includes handheld fine scanning and handheld fast scanning. The handheld fine scanning mode is used to scan high reflective objects by pasting control points on the target, while the handheld fast scanning mode which does not need to paste control points is feasible for scanning general materials. 

## How to anno point clouds
our annotation system is based on open-source software ![CloudCompare](https://www.cloudcompare.org/),As shown in ![anno system](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/anno.png)

## Results
Part of our labeled pointclouds are list in 


