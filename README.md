# spacecraft_3D_component_segmentation_dataset
This project proposes a multi-source 3D component segmentation dataset for non-cooperative spacecraft.
## Where to gain 3D spacecraft models?
 We download the CAD model of the published spacecraft from open-source websites, such as NASA (https://www.nasa.gov/, accessed on 15 March 2022), Free3d (https://free3d.com/, accessed on 15 March 2022), etc. Lately, we print the CAD models utilizing the 3D printing technology to get the 3D printed models.
![CADimage](https://github.com/spacecraft-dataset/spacecraft_3D_component_segmentation_dataset/tree/main/Figure/CAD.pdf)
(Considering the expensive cost of the 3D printing technology, we only print a trivial number of spacecraft CAD models)

## How to gain 3D point clouds?
Simulated point clouds and actual point clouds are obtained. There are three methods to gain 3D point clouds: generating 3D point clouds via AirSim, generating 3D point clouds via SFM, generating 3D point clouds via 3D scanning of spacecraft models. 
### Generation of 3D point cloud via simulation engine
![AirSim](https://microsoft.github.io/AirSim/) is an open-source and cross-platform simulation engine which can imitate the lidar data for multiple different channels. In experiments, lidars of 32 channels are configured on the simulation engine, and parameters are listed in the following Table \ref{airsim_tab}.
