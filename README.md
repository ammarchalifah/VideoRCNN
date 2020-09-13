# RCNN Implementation with Tensorflow 2.3.
![image](https://github.com/ammarchalifah/VideoRCNN/blob/master/video.JPG)<br>
My first task in my first internship was to create an RCNN model that I trained myself. It took more than two weeks during those days.
I tried to find an easy to follow tutorial with up-to-date approach, but I couldn't. After those hardships, finally I'm able to to that
task in significantly shorter time. I was asked to create this very same task for webinar materials from the company I'm working for.
Now, after creating this notebook and model for **Bisa AI Webinar**, I thought it would be really nice if I share this and help
people that desperately need this knowledge. So, here it is: RCNN implementation with TensorFlow 2.3. and Video Processing with RCNN!

## Information
Clone this repository to your Google Drive via Google Colab (or to your local machine, then open it with Jupyter Notebook).
If you use Google Colab, you don't have to install packages yourself because everything is already handled by Google.

## Step by Step
Open the notebook, customize some cells, then run the notebook. Voila. All codes already included in the notebook. But, here is the step-by-step process
under the hood.<br><br>
- First, download the dataset. I use PASCAL VOC2007 dataset with XML annotations. All codes already included in the notebook.
- Second, preprocess the images. I crop the images to foreground and background classes, write them to another directory, and structurize them in train and test directory.
- Third, define the model and start training. Utilize `image_datasets_from_directory` method for handling image datsets from Tensorflow 2.3. I use VGG16 with ImageNet weight as
the feature extractor, with binary classifier fully connected layer.
- Last, evaluate the model and implement it to write bounding boxes over frames from a video.

The directory structure of this project should look like this:
```
├── checkpoints
├── images
|   ├── foreground
|   ├── background
|   ├── train
|   |   ├── background
|   |   └── foreground
|   └── test
|       ├── background
|       └── foreground
└──VOCdevkit
    └──VOC2007
        ├── Annotations
        ├── ImageSets
        ├── JPEGImages
        ├── SegmentationClass
        └── SegmentationObject
```
**Important note:** You have to create the checkpoints and images folder manually (or insert some line of codes in the Colab for that purpose). The VOCdevkit folder
will be created automatically after you download and untar the dataset.
## Limitations
- No Non-max suppression. Single object may have multiple bounding boxes.
- No bounding box regressor. The bounding box size is not optimized to perfectly fit the object.
