In the ubuntu 18.04, the installed path is as below: HOME=/home/${user} For example, the login account is "Tony". The "$HOME" will be "/home/Tony". When installed as root the default installation directory for the Intel Distribution of OpenVINO is /opt/intel/openvino_/. For simplicity, a symbolic link to the latest installation is also created: /opt/intel/openvino/. To shorten the path name, we set various variables here.
```
Setting the following PATH
a=$HOME/openvino_models/ir/intel/face-detection-adas-0001/FP16
b=$HOME/openvino_models/ir/intel/landmarks-regression-retail-0009/FP16
c=$HOME/openvino_models/ir/intel/face-reidentification-retail-0095/FP16
d=$HOME/openvino_models/ir/intel/person-detection-action-recognition-0005/FP16
e=$HOME/openvino_models/ir/intel/person-detection-action-recognition-0006/FP16
f=$HOME/openvino_models/ir/intel/person-detection-raisinghand-recognition-0001/FP16
g=$HOME/openvino_models/ir/intel/person-detection-action-recognition-teacher-0002/FP16

```
Download Model
```
cd /opt/intel/openvino/deployment_tools/tools/model_downloader
sudo python3 downloader.py --name face-detection-adas-0001 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name landmarks-regression-retail-0009 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name face-reidentification-retail-0095 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name person-detection-action-recognition-0005 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name person-detection-action-recognition-0006 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name person-detection-raisinghand-recognition-0001 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name person-detection-action-recognition-teacher-0002 -o $HOME/openvino_models/ir
```
Modeler Optimizer
In this demo, the Model have been converted to .bin and .xml file. You can check it on the following path.
```
$HOME/openvino_models/ir/intel/face-detection-adas-0001/FP16
$HOME/openvino_models/ir/intel/landmarks-regression-retail-0009/FP16
$HOME/openvino_models/ir/intel/face-reidentification-retail-0095/FP16
$HOME/openvino_models/ir/intel/person-detection-action-recognition-0005/FP16
$HOME/openvino_models/ir/intel/person-detection-action-recognition-0006/FP16
$HOME/openvino_models/ir/intel/person-detection-raisinghand-recognition-0001/FP16
$HOME/openvino_models/ir/intel/person-detection-action-recognition-teacher-0002/FP16
```
Inference Engine Sample Compile
```
sudo chown -R username.username $HOME/inference_engine_demos_build
cd $HOME/inference_engine_demos_build
make smart_classroom_demo
```
Excute the application
Download test video from https://github.com/intel-iot-devkit/sample-videos
```
cd $HOME/inference_engine_demos_build/intel64/Release
./smart_classroom_demo -i ~/Downloads/sample-videos-master/head-pose-face-detection-female.mp4 -m_act $d/person-detection-action-recognition-0005.xml -m_fd $a/face-detection-adas-0001.xml -m_reid $c/face-reidentification-retail-0095.xml -m_lm $b/landmarks-regression-retail-0009.xml -fg <path_to_faces_gallery.json> \ -d HDDL
```
