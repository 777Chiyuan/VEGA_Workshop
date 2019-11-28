In the ubuntu 18.04, the installed path is as below: HOME=/home/${user} For example, the login account is "Tony". The "$HOME" will be "/home/Tony". When installed as root the default installation directory for the Intel Distribution of OpenVINO is /opt/intel/openvino_/. For simplicity, a symbolic link to the latest installation is also created: /opt/intel/openvino/. To shorten the path name, we set various variables here.
```
Setting the following PATH
a=$HOME/openvino_models/ir/intel/face-detection-adas-0001/FP16
b=$HOME/openvino_models/ir/intel/age-gender-recognition-retail-0013/FP16
c=$HOME/openvino_models/ir/intel/head-pose-estimation-adas-0001/FP16
d=$HOME/openvino_models/ir/intel/emotions-recognition-retail-0003/FP16
e=$HOME/openvino_models/ir/intel/facial-landmarks-35-adas-0002/FP16
```
Download Model
```
cd /opt/intel/openvino/deployment_tools/tools/model_downloader
sudo python3 downloader.py --name face-detection-adas-0001 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name age-gender-recognition-retail-0013 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name head-pose-estimation-adas-0001 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name emotions-recognition-retail-0003 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name facial-landmarks-35-adas-0002 -o $HOME/openvino_models/ir
```
Modeler Optimizer
In this demo, the Model have been converted to .bin and .xml file. You can check it on the following path.
```
$HOME/openvino_models/ir/intel/face-detection-adas-0001/FP16
$HOME/openvino_models/ir/intel/age-gender-recognition-retail-0013/FP16
$HOME/openvino_models/ir/intel/head-pose-estimation-adas-0001/FP16
$HOME/openvino_models/ir/intel/emotions-recognition-retail-0003/FP16
$HOME/openvino_models/ir/intel/facial-landmarks-35-adas-0002/FP16
```

Inference Engine Sample Compile
```
sudo chown -R username.username $HOME/inference_engine_demos_build
cd $HOME/inference_engine_demos_build
make interactive_face_detection_demo
```
Excute the application
Download test video from https://github.com/intel-iot-devkit/sample-videos
```
cd $HOME/inference_engine_demos_build/intel64/Release
./interactive_face_detection_demo -i ~/Downloads/sample-videos-master/head-pose-face-detection-female.mp4 -m $a/face-detection-adas-0001.xml -m_ag $b/age-gender-recognition-retail-0013.xml -m_hp $c/head-pose-estimation-adas-0001.xml -m_em $d/emotions-recognition-retail-0003.xml -m_lm facial-landmarks-35-adas-0002.xml -d HDDL
```
