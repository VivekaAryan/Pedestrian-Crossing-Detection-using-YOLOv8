# Pedestrian-Crossing-Detection-using-YOLOv8

## Introduction
The safety of pedestrians in smart cities and advanced traffic management systems is of paramount concern in today's world. This report focuses on developing a sophisticated pedestrian detection system aimed at enhancing safety on the roads. This was achieved through fine-tuning the state-of-the-art single-shot object detection YOLOv8s model on an available Pedestrian Intention Estimation (PIE) Dataset, from which we extracted 4922 images, which have three different classes of pedestrians crossing the roads. In order to maintain high standards and yield the best results, the data needed to be prepared and meticulously processed. This training process was evaluated on a plethora of metrics such as bounding box precision, recall, mAP50, mAP50-95, DFL-loss, and classification loss. Our final model was able to achieve a mAP50 of 0.590 and a mAP50-95 of 0.412. The fine-tuned model was used to detect instances in an independent image dataset to simulate real-world scenarios where pedestrians were crossing the roads or not with respect to the ego vehicle.

## Problem Statement
Our goal is to develop an intelligent system that is capable of accurately detecting pedestrians crossing the road. This system is intended to augment the decision-making capabilities of autonomous vehicles (AVs) and thus enhance road safety.

## Dataset

The Pedestrian Intention Estimation (PIE) dataset, a comprehensive resource for studying pedestrian behavior in traffic, was utilized to detect pedestrian crossings. The dataset comprises 6 hours of HD footage recorded in typical traffic settings in Toronto, with varying crowd densities. It includes rich spatial and behavioral annotations for pedestrians and vehicles interacting with the ego-vehicle and environmental elements like traffic lights and signs.

The PIE dataset, chosen over the Joint Attention in Autonomous Driving (JAAD) dataset, is about eleven times larger in terms of frames and offers a higher proportion of annotated frames. It provides detailed pedestrian bounding boxes and behaviors in relation to the ego-vehicle. The dataset consists of six sets, each containing 50 continuous video clips, ensuring a coherent context with a duration of 10 minutes per clip.

Annotations in the PIE dataset include spatial annotations with text labels, object attributes, and ego-vehicle information. Six object classes are meticulously annotated with bounding boxes: pedestrian, vehicle, traffic lights, signs, crosswalk, and transit station. The focus for our specific problem is on spatial annotation related to pedestrian crossings in relation to the ego vehicle, categorized as "crossing," "not-crossing," and "crossing-irrelevant."

![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/9f47f033-85c7-44de-9ad1-5285bf93b8aa)
###### *A sample of different annotations provided in the PIE dataset.*

## Data Preprocessing
Data preprocessing is a crucial phase in developing an object detection model, emphasizing the impact of input data quality on model outcomes. Our project involved meticulous data preprocessing, summarized as follows.

We initially extracted frames from videos, opting for efficiency by working with the first three sets of clips due to storage constraints. Frames were extracted at 1-second intervals, resulting in 4,922 high-quality images. Pedestrian crossing annotations, including unique frame IDs and bounding box coordinates, were retrieved from PIE dataset files. To align with the YOLOv8 model specifications, images were resized to 640x640, requiring corresponding bounding box reshaping.

A Python code partitioned the dataset into train, validation, and test sets (80%, 10%, and 10%, respectively). This facilitated model learning, hyperparameter tuning, and evaluation on unseen data. Bounding data compatible with YOLOv8 was calculated and stored in a JSON file for model use.

For the final preprocessing step, two YAML configuration files were created—one for training and one for testing. These files specify dataset paths, the number of custom classes, and class labels, essential for YOLOv8 model utilization.

![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/71032358-8030-4f26-b402-8b9a729e4c7c)
###### *<center>Sample image along with annotations</center>*
![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/df873244-daaf-45ab-8195-dcb226c7d636)
###### *Sample image in an urban setting along with annotations*
![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/01b0b8d4-0c19-4c76-bb26-383abce350d1)
###### *Sample Image after resizing.*

## Training
We applied transfer learning to boost the YOLOv8 object detection model's performance on our task. By freezing the initial layers during fine-tuning, we preserved the model's prior knowledge. To optimize training efficiency, we employed the Adam optimizer with a momentum of 0.9 and a learning rate of 0.0014. Adjusting epoch and batch size hyperparameters, we experimented with values like 50 and 100 epochs and batch sizes of 16 and 32 images. Due to hardware constraints, our experimentation focused on the YOLOv8n, YOLOv8s, and YOLOv8m models.

![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/25131e42-36be-4486-88d4-f5f97fef0dd7)

## Predictions

#### Prediction 1
![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/769f7365-0a4b-4f0b-9e20-9805ea1933c9)

#### Prediction 2
![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/bf468ab1-a9f0-4464-b906-4af74bc0546b)

#### Prediction 3
![image](https://github.com/VivekaAryan/Pedestrian-Crossing-Detection-using-YOLOv8/assets/52493029/976c7fc3-35f8-4e50-a45a-e912e5ce8d69)




