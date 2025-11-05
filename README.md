# YOLO-Hand-Detection
Scene hand detection for real world images.

### How to Run
To run the model, please first install all the dependencies ([requirements.txt](requirements.txt)) into a virtual environment and download the model and weights into the model folder (or run the shell script).

## Setup a Virtual Environment & source it
```bash
#macOS / Linux
python3 -m venv .venv
source .venv/bin/activate


# Windows (Powershell), under project dir

python -m venv .venv
.venv\Scripts\Activate.ps1
```
### Install Requirements
```
pip install -r requirements.txt
```

```bash
# mac / linux
cd models && sh ./download-models.sh
#chmod +x ./download-models.sh <- run this in case you get a policy error>

# windows
cd models
powershell -ExecutionPolicy Bypass -File ./download-models.ps1

```

Then run the following command to start a webcam detector with YOLOv3:

```bash
# with python 3
python3 demo_webcam.py
```

Or this one to run a webcam detrector with YOLOv3 tiny:

```bash
# with python 3
python3 demo_webcam.py -n tiny
```

For YOLOv3-Tiny-PRN use the following command:

```bash
# with python 3
python3 demo_webcam.py -n prn
```

For YOLOv4-Tiny use the following command:

```bash
# with python 3
python3 demo_webcam.py -n v4-tiny
```
### Idea
To detect hand gestures, we first have to detect the hand position in space. This pre-trained network is able to extract hands out of a `2D RGB` image, by using the YOLOv3 neural network.

There are already existing models available, mainly for MobileNetSSD networks. The goal of this model is to support a wider range of images and a more stable detector (hopefully 🙈).

#### YOLOv3

![Training Graph](readme/chart_yolov3.png)

```
Precision: 0.89 Recall: 0.85 F1-Score: 0.87 IoU: 69.8
```

#### YOLOv3-Tiny

![Training Graph](readme/chart_yolov3-tiny_obj.png)

```
Precision: 0.76 Recall: 0.69 F1-Score: 0.72 IoU: 53.67
```

#### YOLOv3-Tiny-PRN
The tiny version of YOLO has been improved by the [partial residual networks paper](https://github.com/WongKinYiu/PartialResidualNetworks). Because of that I trained YOLO-Tiny-PRN and share the results here too. It is interesting to see that the Yolov3-Tiny-PRN performance **comes close** to the original Yolov3!

![Training Graph](readme/chart_yolov3-tiny-prn.png)

```
Precision: 0.89 Recall: 0.79 F1-Score: 0.83 IoU: 68.47
```

#### YOLOv4-Tiny
With the recent version of YOLOv4 it was interesting to see how good it performs against it's predecessor. Same precision, but better recall and IoU.

![Training Graph](readme/chart_yolov4-tiny.png)

```
Precision: 0.89 Recall: 0.89 F1-Score: 0.89 IoU: 91.48
```





