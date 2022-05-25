# Drowsiness Detection 😴

### 1. Set up and get data
1.1 Follow this guide: https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html <br />
or watch this video: https://www.youtube.com/watch?v=dZh_ps8gKgs&t=1441s <br />
1.2 Clone this repo: https://github.com/nicknochnack/RealTimeObjectDetection <br />
### 2. Annotate images using labelImg package
2.1 Clone this repo inside "Drowsiness/Tensorflow": https://github.com/tzutalin/labelImg <br />
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
### 3. Partition augmented data (images + label files) manually in train and test folder (the ratio is 9:1) 
### 4. Use Augmentor library to augment images in vertically, horizontally, etc.
4.1 Install Augmentor using pip
```
pip install Augmentor
```
4.2 Import Augmentor
```
import Augmentor as A
```
4.3 Adding operations to a pipeline
```
p = A.Pipeline("Tensorflow/workspace/images/train") or p = A.Pipeline("Tensorflow/workspace/images/test")
```
4.4 Then add operations to the Pipeline object p as follows:
```
p.flip_left_right(probability=0.5)
p.greyscale(probability=0.2)
p.random_contrast(probability=0.2, min_factor=0, max_factor=255)
p.skew_left_right(probability=0.5)
p.resize(probability=1.0, width=320, height=320)
```
4.4 Executing a pipeline
```
num_of_samples = int(6000)
# Now we can sample from the pipeline:
p.sample(num_of_samples)
```
### 5. Transfer learning using SSD MobileNet V2 
### 6. Train and evaluate the model
### 7. Use tensorboard to analyse the train and evaluate result 
### 8. Detect drowsiness using an image 
### 9. Real time drowsiness detection using a webcam with OpenCV 
