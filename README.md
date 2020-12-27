# Introduction
This is a github for NCTU course "Selected Topics in Visual Recognition using Deep Learning" homework Final: Global Wheat Detection.
I refer to facebook's contribution, detectron2.
All of my homework was completed and can be train/predict in Google colab and predict Kaggle.

# My Homework Program
The program I made in Google colab is based on facebook detectron2's colab tuturial program.

[my homework colab](https://colab.research.google.com/drive/1mPiyNd4Y10qPU0GTia9k5CkEyTpTo-Er?usp=sharing)

[Kaggle Competition](https://www.kaggle.com/wangchilung/detectron2-for-global-wheat-detection)

# README

1. Install pytorch and detectron.
2. After detectron2 installed, the runtime needs to be restarted. Thus you can see a code exit(0) to restart the runtime and an error message: "你的工作階段因不明原因而異常終止。" shown. This is a correct result. There is no problem to go on executing the program.
3. Please wait the jupyter notebook reconnect and then you can go on the following execution.
4. The program will download the dataset, global-wheat-detection.zip, from my repository.
5. You can see the number of train dataset images is 3422 and test dataset images is 10. There are only 3733 images with label and the number of label records is 147793
6. Two functions `image_name2id` and `image_id2name` are used to map image filename to image id. And yet another two functions `class_name2id` and `class_id2name` to transfer between dataset category name and dataset category id.
7. In detectron2, if the dataset follows coco format, we can simply use the function to register the dataset:
<pre><code>register_coco_instances('wheat_train', {}, 'wheat_train_coco.json', './')
register_coco_instances('wheat_valid', {}, 'wheat_valid_coco.json', './')</code></pre>
8. In `get_wheat_dicts`, we split the 3422 samples in train dataset into train dataset (2698 samples) and validate dataset (675 samples) and specify by the third parameter 'train' or 'valid'.
9. In train phase, we can train the model from scratch or resume the training process.
10. We adopt the data augmentation of `RandomFlip`, `RandomBrightness`, `RandomContrast`, `RandomLighting` and `RandomRotation`.
11. In every certain of epoches, we validate the mAP by using valid dataset.
12. The train dataset are also used to verify the mAP and submission jason format as well.
13. In Prepare submission file section, each instance is recorded in the list of `image_id` and `PredictionString`.
14. The final submission file can be obtained from the file of `./submission.json`.
