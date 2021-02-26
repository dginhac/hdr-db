# HDR-DB : A versatile HDR database

Welcome to the HDR-DB Site! 

We propose, free of charge, a versatile video database and also a framework able to generate automatically HDR video content according to user settings. This framework typically includes a set of Matlab scripts to process HDR videos from multiple LDR exposures. It can offer several user-tunable parameters such as the desired quantity of movement in the scene, the dynamic range selection or the number of sequential exposures to be used in the HDR generation.The framework can be used to generate a HDR video from sequential exposures with artificially introduced ghost artifacts(i.e. temporal dependant artifacts), along with a reference of a ghost-free HDR video for ground truth. This database, coupled with the other processing steps of the HDR creation pipeline(Hdr merge and tone mapping), could be used as a platform to test and benchmark deghosting algorithms

# Download

* Step 1: The [HDR toolbox](https://github.com/banterle/HDR_Toolbox) by Banterle et al. is required. 
* Step 2: Download the [HDR Database](http://hdr-db.u-bourgogne.fr/HDR_Database.zip)  ~2GB

# Installation and Usage

1. Install the HRD toolbox using the provided script 
2. Unzip the HDR database and run the script, script.m under Matlab. Follow the indication and answer the differents questions. 
3. « Et voila » video sequences are generated and can be used to test deghosting algorithms. 

# Features

Main features of the HDR video database are: 

1. Generate LDR and/or HDR video content from a global LDR database, given a desired number of exposures, dynamic range or relative quantity of movement between video frames,
2. Visualize the results after tone mapping for both "ghosted" or "deghosted" video,
3. Display information about the reconstructed video, i.e. number of low/high saturated pixels , relative dynamic range captured, etc.

# Data Capture

The camera used for the database acquisition is a DSLR Nikon D700, featuring a 4,256 x 2,832 pixesl image sensor. All the camera settings are fixed during the acquisition of the successive shots of the scene, except the exposure times that are changed every time a new bracketed image is acquired. Note that there are three main ways to adjust camera settings in order to control the amount of light captured. One is to change the shutter speed, i.e the exposure time, another is to change the aperture, and the third is to change the ISO sensibility. 

Varying the aperture or the ISO sensitivity does not only change the amount of light captured but also changes the depth of field for the aperture and the amount of noise for ISO. So, in our case, the optical aperture has been fixed to F/4.0 and the ISO to 200. 

Finally, the exposure set is composed of a maximum of 9 images taken with a 1 EV spacing, which represent a total dynamic range of 17 EV for each time-lapse. The image data are stored in 14-bit uncompressed RAW files in order to preserve the highest quality. Following this protocol, a total of 486 frames are recorded in our database, distributed over 54 time-lapses (486/9).

#Video creation

The original setup work-flow is dedicated to visual quality assessment on the resulting LDR/HDR processing. After downloading the HDR-db database, Matlab scripts can be processed to reconstruct customized LDR or HDR video content following user settings. Scripts can be tuned as follows:

**Output video** type is 'sequential LDR', 'HDR' or 'HDR tone mapped' image/video set. The HDR data container output is a folder with several images sequentially organized for video viewing. The data types are respectively a 14-bit RAW format for LDR images and OpenEXR format for HDR images. OpenEXR is an open-source HDR file format under BSD license, specifically developed for high-quality storage and processing. OpenEXR offers also some direct image processing for visualization and customization of HDR data. 'LDR' and 'sequential LDR' are directly outputted in .avi format for direct visualization, 

**Quantity of motion** in the scene is fixed by defining the gap number between single shots when reconstructing the videos. This gap number can be 0, 1, 2, 3, 4, 5 ... Based on a stop motion technique, the increment of motion is constant between single shots. So, the resulting quantity of motion increases proportionally with the gap number.

**Number of LDR exposures** to reconstruct the LDR/HDR video set is between 1 and 9 images. High quality requirements involve to chose enough exposures to cover the full dynamic range of the scene but also to chose not to many exposures in order to minimize ghosting effects. 

**Exposure times** is in the range [-4,-3,-2,-1,0,1,2,3,4] for light stops, according to the number of selected LDR exposures. The database provides images with 1-stop regular spacing but user can freely select any combination of exposure times. 

# Post-processing

Displaying HDR images/videos still remains a technological challenge since most of monitors feature a relatively small dynamic range. So, this issue has given rise to the active research area of tone mapping, in which the dynamic range of the HDR images/videos is reduced so that it matches the range of the monitor. So, to visualize the results of the HDR video creation step, several tone mapping algorithms can be chained to the processing pipeline. Five different tone mapping operators are available in our processing framework.
Tone mapping operators could be global or local. Global operators mean that the same processing function is applied to every pixel of the image. In contrast, local operators use spatially varying processing for each pixel, considering the values of the neighborhood, for a better rendering in term of details.

Since our work does not focus on tone mapping operators, we have decided to re-use tone mapping algorithms available in the HDR Toolbox by Banterle et al. . However, other operators could be easily implemented by contributors.

# Contact

e-mail: dginhac@u-bourgogne

url: http://hdr-db.u-bourgogne.fr
