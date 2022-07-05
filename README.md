# Drowsiness Detection 😴

### 1. Set up and get data
1.1 Follow this guide: https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html <br />
or, watch this video: https://www.youtube.com/watch?v=dZh_ps8gKgs&t=1441s <br /> <br />
1.2 Clone this repo using this command:
```
git clone https://github.com/nicknochnack/RealTimeObjectDetection
```
### 2. Annotate images using labelImg package
2.1 Clone this repo inside e.g. "Drowsiness/Tensorflow" using this command: 
```
git clone https://github.com/tzutalin/labelImg 
```
2.2 Setup labelImg for Windows:
```
conda install pyqt=5
conda install -c anaconda lxml
pyrcc5 -o libs/resources.py resources.qrc
python labelImg.py
python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```
2.3 Run labelImg by giving the path
```
!cd Tensorflow/labelImg && python labelImg.py
```
### 3. Use Augmentor library to augment images vertically, horizontally, etc.
3.1 Install Augmentor using pip
```
pip install Augmentor
```
3.2 Import Augmentor
```
import Augmentor as A
```
3.3 Adding operations to a pipeline
```
p = A.Pipeline("Tensorflow/workspace/images/train") or p = A.Pipeline("Tensorflow/workspace/images/test")
```
3.4 Then add operations to the Pipeline object p as follows:
```
p.flip_left_right(probability=0.5)
p.greyscale(probability=0.2)
p.random_contrast(probability=0.2, min_factor=0, max_factor=255)
p.skew_left_right(probability=0.5)
p.resize(probability=1.0, width=320, height=320)
```
3.5 Executing a pipeline
```
num_of_samples = int(6000)
# Now we can sample from the pipeline:
p.sample(num_of_samples)
```
### 4. Partition augmented data (images + label files) manually in train and test folder (the ratio is 9:1) 
### 5. Transfer learning using SSD MobileNet V2 
### 6. Train and evaluate the model
Once you use the training command in the Windows OS terminal, you will start to get the loss metrics (classification, localization, regression, total loss) like below:
![WhatsApp Image 2022-01-03 at 8 19 34 AM](https://user-images.githubusercontent.com/89456649/170283125-80223108-7f64-436c-8cf0-5f552551f98b.jpeg)

Next, run the evaluation command to analyze the train data inside the Windows terminal, you will start to see eval metrics like the below:
![WhatsApp Image 2022-01-17 at 10 50 48 PM (1)](https://user-images.githubusercontent.com/89456649/170283473-7b86fdf2-d929-4654-8b96-e6b19ab196d5.jpeg)
### 7. Use tensorboard to analyze the train and evaluate the result
7.1 Navigate to the train folder for your trained model e.g.
```
cd Drowsiness/Tensorlfow/workspace/models/my_ssd_mobnet/train
```
7.2 Then, open Tensorboard with the following command
```
tensorboard --logdir=.
```
7.3 Navigate to the evaluation folder for your trained model e.g.
```
cd Drowsiness/Tensorlfow/workspace/models/my_ssd_mobnet/eval
```
7.4 Similarly, open the tensorboard to eval the data
### 8. Detect drowsiness using an image
![download](https://user-images.githubusercontent.com/89456649/170284542-86634dfe-3c03-4955-8ef6-6a5f741369e4.png)
### 9. Real time drowsiness detection using a webcam with OpenCV
https://user-images.githubusercontent.com/89456649/177331318-f2e6d4da-e2fb-4013-a73a-dafc73dcb6ac.mp4
