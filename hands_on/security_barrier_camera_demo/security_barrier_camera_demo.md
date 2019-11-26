## Security barrier camera

In the ubuntu 18.04, the installed path is as below:
HOME=/home/${user}
For example, the login account is "Tony". The "$HOME" will be "/home/Tony".
When installed as root the default installation directory for the Intel Distribution of OpenVINO is /opt/intel/openvino_<version>/.
For simplicity, a symbolic link to the latest installation is also created: /opt/intel/openvino/.
To shorten the path name, we set various variables here.
```
openvino_dir=/opt/intel/openvino
vehicle-license-plate-detection-barrier-0106=$HOME/openvino_models/ir/intel/vehicle-license-plate-detection-barrier-0106/FP16
vehicle-attributes-recognition-barrier-0039=$HOME/openvino_models/ir/intel/vehicle-attributes-recognition-barrier-0039/FP16
license-plate-recognition-barrier-0001=$HOME/openvino_models/ir/intel/license-plate-recognition-barrier-0001/FP16
```
#### Download  Model
```
cd /opt/intel/openvino/deployment_tools/tools/model_downloader
sudo python3 downloader.py --name 
sudo python3 downloader.py --name vehicle-license-plate-detection-barrier-0106 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name vehicle-attributes-recognition-barrier-0039 -o $HOME/openvino_models/ir
sudo python3 downloader.py --name license-plate-recognition-barrier-0001 -o $HOME/openvino_models/ir
```

#### Moder Optimizer
#### Model Optimizer
In this demo, the Model have been converted to .bin and .xml file.
You can check it on the following path.
$HOME/openvino_models/ir/intel/vehicle-license-plate-detection-barrier-0106/FP16
$HOME/openvino_models/ir/intel/vehicle-attributes-recognition-barrier-0039/FP16
$HOME/openvino_models/ir/intel/license-plate-recognition-barrier-0001/FP16
```
```

#### Inference Engine Sample Compile

```
sudo chown -R username.username $HOME/inference_engine_demos_build
cd $HOME/inference_engine_demos_build
make security_barrier_camera_demo
```

#### Excute the application

```
cd $HOME/inference_engine_demos_build/intel64/Release
./security_barrier_camera_demo -i $openvino_dir/deployment_tools/demo/car_1.bmp -m $vehicle-license-plate-detection-barrier-0106/vehicle-license-plate-detection-barrier-0106.xml -m_va $vehicle-attributes-recognition-barrier-0039/vehicle-attributes-recognition-barrier-0039.xml -m_lpr $license-plate-detection-barrier-0106/license-plate-detection-barrier-0106.xml -d HDDL
