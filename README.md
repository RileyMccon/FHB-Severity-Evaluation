# FHB-Severity-Evaluation

This project focuses on developing a new method to evaluate FHB severity in wheat. It combines the use of deep learning object detection and instance segmentation models, with traditional remote sensing techniques, to produce an accurate and reproducible method to estimate FHB severity. This was first tested using images of single wheat heads infected with FHB. The "YOLOv8 wheat head detection model training" file shows the source code used to train an object detection model to localize the single wheat heads within the image. In addition, an instance segmentation model was trained in the "YOLOv8 wheat head instance segmentation model training" file to segment the healthy and infected tissue within the heads. The models produced through these scripts can be found in the " Wheat_Detection" and the "Wheat_Segmentation" files respectively. 
Meta's Segment Anything Model (SAM) was then used to produce instance segmentation masks of the single heads, using the object detection model as an input. The accuracy of these masks was tested against ground truth masks in the "SAM Accuracy" file. The SAM model is available to download from their GitHub page https://github.com/facebookresearch/segment-anything. As seen in the "Severity Estimation" file, following segmentation a transformation was applied to the heads using the red and green radiance values. A threshold was then determined to separate healthy from infected tissue within the heads, and the pixels within each category were counted to estimate severity within the heads. Stratified random sampling was then used to determine the accuracy of the pixel classification within the images. 
This methodology was then tested for its transferability in the "Transferability Testing" file, using images taken as part of another study (available from https://github.com/cvims/FHB_classification). In addition, a different wheat head detection model was used as these images consisted of wheat plots in the field. This model was developed as part of the Global Wheat Challenge and is available to download from https://github.com/ksnxr/GWC_solution (to learn about their study please see their publication: https://doi.org/10.34133/2021/9846158). Similar to the single-head images, a threshold was found for the plot-level images and stratified random sampling was completed to determine the accuracy of the index used. 