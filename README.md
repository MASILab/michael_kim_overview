# michael_kim_overview
Overview of all projects by Michael Kim (kimm58)



## 1.) An Empirical Assessment of the Assumptions of ComBat with Diffusion Tensor Imaging

Github: https://github.com/MASILab/Diff_MRI_Harmonization.git

Data: backup via amazon (ADSP)

Paper: https://www.spiedigitallibrary.org/journals/journal-of-medical-imaging/volume-11/issue-02/024011/Empirical-assessment-of-the-assumptions-of-ComBat-with-diffusion-tensor/10.1117/1.JMI.11.2.024011.full

This was my first research project, looking at performance of the ComBat algorithm for site-wise harmonization when using Diffusion MRI data. We assessed performance using a well-matched dataset from two different sites (VMAP, BLSA) as a baseline, then performed a bootstap analysis of how varying sample size, sample size imbalance, and covariate shift/overlap affect the estimates of association of Age with fractional anisotropy (FA) and mean diffusivity (MD), and the site-estimated shift and scale of the harmonized features (which were the FA/MD of regions in the EVE3 WMAtlas). Our analyses demonstated that ComBat performance is worse than expected for diffusion MRI data (i.e. need a larger sample size and tighter covariate overlap) in order to get estimates from ComBat that do not deviate too far from the well-matched scenario. 


## 2.) Characterizing Low-cost Registration for Photographic Images to Computed Tomography

Github: https://github.com/MASILab/DeformableSurfaceReg.git

Data: XNAT: NeRF_Surface_Landman: https://xnat.vanderbilt.edu/xnat/data/projects/NeRF_Surface_Landman

Paper: https://medicalimaging.spiedigitallibrary.org/proceedings/Download?urlId=10.1117%2F12.3005578&downloadType=proceedings%20article&isResultClick=True
https://www.biorxiv.org/content/10.1101/2023.09.22.558989v1


SPIE 2024 paper - A characterization of low-cost photogrammetry techniques for surface reconstruction. Using surfaces obtained from CT images as the ground truth, we assess the quality of the photogrammetry surfaces obtained from Neural Radiance Fields (NeRF, as instant-ngp implementation) and the VECTRA H1 3D Imaging System of a hip implant, a knee implant, and a steak.  First, we register the photogrammetry surfaces to the ground truth CT. We then use fiducial registration error and average surface distance as metrics to assess quality. We find that the H1 camera provides smooth surfaces, but cannot reconstruct objects that are larger or have sharp changes in geometry. Whereas NeRF has the capability to capture finer detail, the surfaces are much noisier and more artifact-prone. Our conclusion was that NeRF-based methods have the greater potential, but improvements need to be made to the implementation.


## 3.) Characterization of Neural Radiance Field-Based 3D Reconstruction of Organ Tissue Surfaces (technical paper)

Github: https://github.com/MASILab/DeformableSurfaceReg.git

Data: XNAT: NeRF_Surface_Landman: https://xnat.vanderbilt.edu/xnat/data/projects/NeRF_Surface_Landman


Extension of SPIE 2024 - Characterization of NeRF-based techniques for reconstruction of human organ tissue surfaces. We assess multiple points in the processing pipeline (image acquisition and surface reconstruction) to determine what aspects of organ surfaces make reconstruction difficult and what solutions work best to optimize surface reconvery. We find that addition of external features in the image scene help with feature matching of the images, particularly when only adding a few eternal fiducials. We also find that modification of the specular estimator of the nerf2mesh implementation did not provide better surface recovery. However, having a high laplacian regularization helps remove/alleviate areas of low-density estimation. Building a shape model to fix the estimated density field also did not provide a successful solution.

## EXTRA: ADSP/R01 Diffusion Data Organization

Github: https://github.com/MASILab/Diff_MRI_Harmonization.git (and R01_Data_Organization)

Organized and preprocessed the majority of the datasets for the ADSP/R01 grants. Created a script generator that allows for easy and standardized preprocessing of data on ACCRE (or locally as well), given that data is in BIDS format. Also created a few query tools that do various tasks, such as summarize the preprocessing that has been run, number of shells, etc.

## EXTRA: Atlas Registration from T1 space to Diffusion Space

Github: https://github.com/MASILab/AtlasToDiffusionReg

Created a singularity for deformably registering an atlas to a diffusion scan of a subject using ANTs, fsl, c3d, etc. Requires a T1, a segmentation of the T1 (SLANT preferrably), the preprocessed DWI scan, the structural template and the labelmap/atals, and label files for both the segmentation and the labelmap/atlas. Outputs the transformations and registered atlas, as well as a CSV of the mean, median, and stdev of the tensor metrics for FA, MD, AD, RD.
