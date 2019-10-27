# adl4cv
Im2Flow hallucinating motion model for Tracktor++

Abstract:

The paper “Tracking without bells and whistles” proposes a new multi-object tracking method called Tracktor. 
At its core the bouding box regression capabilites of a state-of-the-art object detection network such as Faster R-CNN are exploited to predict the position of the object in the next frame.

In Tracktor++ a constant velocity assumption (CVA) is used for videos with low frame rates. To improve this motion model to support  Tracktor in difficult cases of reID. Based on the Im2Flow paper we want to use the MOT17 dataset to train an additional regressor that hallucinates the motion of pedestrians and thus predicts current position of occluded objects given only (e.g.) every tenth frame. For training the motion model regressor we will use trajectories that are fully observed as well as those that contain occlusions. In these cases the ground truth is linearly interpolated using the bounding boxes before and after an occlusion event. 

Im2Flow predicts the optical flow of a scene based on static images.

Training set of Im2Flow:

    Input: single static image from a video sequence

    Output: optical flow obtained from the video sequence

 In this project we will focus on pedestrians in the MOT17 dataset so that we will use the Im2Flow architecture and we anticipate that by limiting the variation of motion to standing, walking and running our Im2Flow regressor could work using less model complexity. If time allows we hope to exploit this and reduce the model complexity so it can be performed online and be used as an online extension of Tracktor.

References:

    Faster R-CNN: https://arxiv.org/abs/1506.01497

    Tracktor: https://arxiv.org/abs/1903.05625

    Tracktor-Code: https://github.com/phil-bergmann/tracking_wo_bnw

    MOT-Data: https://motchallenge.net/

    Im2Flow: Motion Hallucination from Static Images for Action Recognition: https://arxiv.org/abs/1712.04109


Initial Steps:

    Visualize MOT17 dataset

    Try dataset generation idea

    Figure out and set up cloud infrastructure

    Train the Tracktor++ model on MOT17 using the available GitHub repository and understand the CVA motion model interface

    Understand Im2Flow paper: optical flow encoding and network architecture

    Reimplement Im2Flow model



Milestones:

    Establish Tracktor as baseline using MOT17 as dataset using the existing github implementation

    Generate a dataset from MOT17 with single frames as input and an optical flow estimation using the bounding box in step t and t+1 (direction and speed of movement) potentially for individual pedestrians by cropping the images to the bounding boxes

    Reimplement Im2Flow model and thoroughly understand optical flow encoding 

    Train a motion hallucinator model based on the Im2Flow architecture and using the generated dataset

    Extend or replace the CVA motion model in Tracktor++ with the prediction of the motion hallucinator
