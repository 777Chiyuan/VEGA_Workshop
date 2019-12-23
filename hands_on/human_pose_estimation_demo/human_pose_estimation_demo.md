In the ubuntu 18.04, the installed path is as below: HOME=/home/${user} For example, the login account is "Tony". The "$HOME" will be "/home/Tony". When installed as root the default installation directory for the Intel Distribution of OpenVINO is /opt/intel/openvino_/. For simplicity, a symbolic link to the latest installation is also created: /opt/intel/openvino/. To shorten the path name, we set various variables here.
```
Setting the following PATH
a=$HOME/openvino_models/ir/intel/human-pose-estimation-0001/FP16
```
Download Model
```
cd /opt/intel/openvino/deployment_tools/tools/model_downloader
sudo python3 downloader.py --name human-pose-estimation-0001 -o $HOME/openvino_models/ir
```
Modeler Optimizer In this demo, the Model have been converted to .bin and .xml file. You can check it on the following path.
```
$HOME/openvino_models/ir/intel/human-pose-estimation-0001/FP16
```
Inference Engine Sample Compile
```
sudo chown -R username.username $HOME/inference_engine_demos_build
cd $HOME/inference_engine_demos_build
make human_pose_estimation_demo
```
Excute the application Download test video from https://github.com/intel-iot-devkit/sample-videos
```
cd $HOME/inference_engine_demos_build/intel64/Release
./human_pose_estimation_demo -i ~/Downloads/sample-videos-master/worker-zone-detection.mp4 -m $a/human-pose-estimation-0001.xml -d HDDL
```
