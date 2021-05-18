# Flip Learning: Erase to Segment

A weakly-supervised segmentation method based on `Reinforcement Learning` that only needs bbox label.

## Framework

The workflow of our proposed method. 
![image](https://github.com/goloooo777/flip-learning/blob/main/images/framework.png)

## Environment

* Python  
* Pytorch  
* OpenCV  
* Gym  

## Usage

Codes will be released soon.

## Results
1. Examples of superpixels. The first row shows the coarse superpixels, and the second row shows the corresponding fine superpixels.
![image](https://github.com/goloooo777/flip-learning/blob/main/images/superpixel.png) 

2. Results of two stages. The right corner figures show the superpixels and the erased areas are marked in blue.
![image](https://github.com/goloooo777/flip-learning/blob/main/images/result_stage.png) 

3. Two testing cases of multi-agent erasing (stage 2). The blue bbox contains the nodule to be segmented. The red and green bboxes are two agents. They traverse the superpixels with actions including 1) erasing (solid yellow bbox) and 2) passing (hollow yellow bbox).

* Case1  
<p float="left">
    <img src="https://github.com/goloooo777/flip-learning/blob/main/images/1_image.gif" width="200"/><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/1_gt.png" width="200"/><img src="https://github.com/miccai-1545/flip-learning/blob/main/images/1_pred.png" width="200"/>
</p>



* Case2  
![image](https://github.com/goloooo777/flip-learning/blob/main/images/2_image.gif)  
![image](https://github.com/miccai-1545/flip-learning/blob/main/images/2_gt.png)  
![image](https://github.com/miccai-1545/flip-learning/blob/main/images/2_pred.png) 

4. Visualization of classification tag flipping . The left figure shows the original image with the tag 'Nodule' and the erasing process. The middle one visualizes the erasing curve including erasing area, classification score of nodule and DICE in each step. The last figure shows the image after tag flipping (i.e., with tag 'Normal tissue'). 
![image](https://github.com/goloooo777/flip-learning/blob/main/images/tag_flipping.gif)


