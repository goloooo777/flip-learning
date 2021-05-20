# Flip Learning: Erase to Segment

A weakly-supervised segmentation method based on `Reinforcement Learning` that only needs bbox label.

## Framework

The workflow of our proposed method. 
![image](https://github.com/miccai-1545/flip-learning/blob/main/images/framework.png)

## Environment

* Python  
* Pytorch  
* OpenCV  
* Gym  

## Usage 

### Dataset Setting

```
-- data  
   --- subjects1  
       --- data.png # the original image
       --- data_crop.png # the background image generated by the crop-paste method
       --- nodule.npy  # the BBox information: (x1,y1,x2,y2)
       --- mask.png  # for evaluation only [Not required in the testing phase!]
   ...
```
### Testing

We have uploaded the testing software (*exe* format) to OneDrive: https://1drv.ms/u/s!AowDfwnjiDZrbNK6AJOQ-4XcdDc?e=0n1skz and provide some testing cases in *testing images* filefolder.

<div align=center><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/demo.png"></div>  

The function of our testing software is shown as followed:  
- Input image  
`Load:` Load the image to be segmented.  
- Visualization-pre (pre-process)  
`BBox:` Visualize the BBox on the image.  
`Superpixel:` Visualize the superpixel on the image. If *mask.png* exists, the nodule boundary will be drawn.  
- Visualization-result (predicted result)  
`Predict-m:` Visualize the mask after post-process (erode/hole-filling/dilate).  
`Predict-o:` Visualize the predicted mask boundary on the original image.  
`Predict-c:` If *mask.png* exists, compare the boundaries of predicted mask and ground truth on the original image.  
`Predict-f:` Visualize the erased image with the tag 'Normal tissue' instead of 'Nodule'.  
`Predict-e:` If *mask.png* exists, draw the erasing curve (each step) including DICE, classification score, and erased area.
  
- Visualization-gif     
`Gif-erasing:` Visualize the multi-agent erasing process.

The predictions and visualization results will be stored in the *save* filefolder.

## Results
1. Examples of superpixels. The first row shows the coarse superpixels, and the second row shows the corresponding fine superpixels.  

<div align=center><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/superpixel.png"></div>  

2. Results of two stages. The right corner figures show the superpixels and the erased areas are marked in blue.  

<div align=center><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/result_stage.png"></div>  

3. Two testing cases of multi-agent erasing (stage 2). The blue bbox contains the nodule to be segmented. The red and green bboxes are two agents. They traverse the superpixels with actions including 1) erasing (solid yellow bbox) and 2) passing (hollow yellow bbox). From left to right show the multi-agent erasing process, ground truth and prediction, respectively.
 
* Case1     
<p float="center">
    <div align=center><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/1_image.gif" width="250"/><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/1_gt.png" width="250"/><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/1_pred.png" width="250"/></div>  
</p float="center">

* Case2  
<p float="center">
    <div align=center><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/2_image.gif" width="250"/><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/2_gt.png" width="250"/><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/2_pred.png" width="250"/></div>  
</p>


4. Visualization of classification tag flipping . The left figure shows the original image with the tag 'Nodule' and the erasing process. The middle one visualizes the erasing curve including erasing area, classification score of nodule and DICE in each step. The last figure shows the image after tag flipping (i.e., with tag 'Normal tissue').  

<div align=center><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/tag_flipping.gif"></div> 



