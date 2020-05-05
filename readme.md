# Tensorflow inferences with Azure Custom Vision
* prototyping image recognition inference with Azure Custom Vision (ACS) and Tensorflow
  * ACS... because very easy to training, and can export model-file outside of cloud.
  * Tensorflow... Including Tensorflow lite (to run on an Edge)

# How to run
## Training on ACS(Azure Custom Vision) and export tensorflow model
* based on [Quickstart: How to build a classifier with Custom Vision](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier)
* [my sample](exported_savedmodel)

## run inference on laptop (with Tensorflow exported model)
* [With sample.jpg](tf_inference_from_localjpg.py)
* [With Local camera (OpenCV VideoCapture)](tf_inference_from_videocapture.py)
* based on [Tutorial: Run TensorFlow model in Python](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/export-model-python)
* using "TensorFlow" format.

## convert model on laptop (with Tensorflow)
* [convert_from_savedmodel.py](convert_from_savedmodel.py)
* using "SavedModel" format.

## run inference on Edge (with converted model and Tensorflow lite on Laptop or Edge PC)
* [With sample.jpg](tflite_inference_from_localjpg.py)
* [With Local camera (OpenCV VideoCapture)](tflite_inference_from_videocapture.py)
* before run, install tensorflow lite runteime and change import section as below:
```(py)
# from tensorflow import lite as tflite  # on Laptop
import tflite_runtime.interpreter as tflite  # on Edge
```
* Install Tensorflow lite references
  * [Python quickstart](https://www.tensorflow.org/lite/guide/python)
  * Other resources: [TensorFlow Lite inference](https://www.tensorflow.org/lite/guide/inference)
* I tested on Raspberi pi 3 b+

## !Notes
* using classification model only in this repo
  * Not deploying detection model yet


# ToDo list
## Must
- [x] run tutorial code  
- [x] run tutorial code on cv2.VideoCapture  
- [x] converting exported model to tflite  
- [x] run videocapture inference with tflite (on Laptop)  
- [x] build tflite env on edge (Raspi3)  
- [x] run videocapture inference with tflite (on edge)  
- [ ] run inference codes with Coral TPU  
- [ ] more... ?  
## if possible
- [ ] try again with tflitemodel from ACS directory (I tested onece, but failed)  
- [ ] record inference time  
- [ ] converting [tutorial code](tutorial_videocapture.py) based on tf2.0  
## motivation
* I want to learn
  * inference engine with Tensorflow lite
  * how edge AI run
  * how efficient is Coral Edge TPU
