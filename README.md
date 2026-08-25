# TEMP WIP README
Good luck wıth the Turkısh lol


```


source ~/colcon_ws/install/setup.bash
ros2 run ros_tcp_endpoint default_server_endpoint

cd /home/kaplan/colcon_ws/src/smarc2
chmod +x 
python3 

kolu bağlamak için:
-unity aç
-köprüyü aç : ros2 run  ros_tcp_endpoint default_server_endpoint 
-kolu aç: ros2 run joy joy_node --ros-args -p deadzone:=0.08 -p autorepeat_rate:=20.0
-kodu başlat: python3 ps5....


mavros başlat:
# ROS 2 ve MAVROS workspace'ini aç:
source /opt/ros/jazzy/setup.bash

# MAVROS'u başlat:
ros2 run mavros mavros_node \
  --ros-args \
  -p 'fcu_url:=udp://0.0.0.0:14551@'

# kontrol et
ros2 topic list | grep 'mavros/state'

# Bağlantıyı kontrol et:
ros2 topic echo xxxxx --once


manualControl topic???
ros2 topic list | grep manual_control

ros2 topic info /mavros/manual_control/send -v
#MAVROS should be seen as subscriber

twist-manual kodunu çalıştır

source /opt/ros/jazzy/setup.bash
source ~/rov_ws/install/setup.bash

ros2 run rov_autonomy twist_to_manual_control



YOLO
source /opt/ros/jazzy/setup.bash
source ~/colcon_ws/install/setup.bash

ros2 run ros_tcp_endpoint default_server_endpoint

ros2 run rqt_image_view rqt_image_view

MANUAL CONTROL ECHO

source /opt/ros/jazzy/setup.bash
ros2 topic echo /mavros/manual_control/send



movement twist 

timeout 2s ros2 topic pub --rate 20 \
/rov/autonomy/cmd_vel \
geometry_msgs/msg/Twist \
"{linear: {x: 0.1, y: 0.0, z: 0.0},
  angular: {x: 0.0, y: 0.0, z: 0.0}}"
  
timeout 2s ros2 topic pub --rate 20 \
/rov/autonomy/cmd_vel \
geometry_msgs/msg/Twist \
"{linear: {x: 0.0, y: 0.0, z: 0.0},
  angular: {x: 0.0, y: 0.0, z: 0.0}}" 
  
  
  
  


ros2 launch alars_auv_perception alars_yolo_detector.launch.py \
  robot_name:=ActiveHook_6T \
  device:=cpu \
  use_sim_time:=false \
  model_package:=alars_labeling_training \
  model_file:=yolo_model_2cls_mixed.pt \
  raw_image_topic:=/ActiveHook_6T/camera/image_raw
  
  
  
  twist to manual control test;
  
  #mavros
  
source /opt/ros/jazzy/setup.bash
ros2 run mavros mavros_node \
  --ros-args \
  -p 'fcu_url:=udp://0.0.0.0:14551@'
  
  #topic check et
source /opt/ros/jazzy/setup.bash

ros2 topic echo /mavros/state

  #twist_to_manual_control
source /opt/ros/jazzy/setup.bash
source ~/rov_ws/install/setup.bash

ros2 run rov_autonomy twist_to_manual_control


  #manual_control msg
source /opt/ros/jazzy/setup.bash

ros2 topic echo /mavros/manual_control/send


  #motor_outputs
source /opt/ros/jazzy/setup.bash

ros2 topic echo /mavros/rc/out

  
  #neutral test
timeout 3s ros2 topic pub --rate 20 \
/rov/autonomy/cmd_vel \
geometry_msgs/msg/Twist \
"{linear: {x: 0.0, y: 0.0, z: 0.0},
  angular: {x: 0.0, y: 0.0, z: 0.0}}"
  
  
  #ARM IN TERMINAL
ros2 service call /mavros/cmd/arming \
mavros_msgs/srv/CommandBool \
"{value: true}"

  #disarm ofcourse
ros2 service call /mavros/cmd/arming \
mavros_msgs/srv/CommandBool \
"{value: false}"

  #forward command
timeout 3s ros2 topic pub --rate 20 \
/rov/autonomy/cmd_vel \
geometry_msgs/msg/Twist \
"{linear: {x: 0.05, y: 0.0, z: 0.0},
  angular: {x: 0.0, y: 0.0, z: 0.0}}"
  
  
  
  
 
 
 source everything

source /opt/ros/jazzy/setup.bash
source ~/rov_ws/install/setup.bash


1. ADIM

source /opt/ros/jazzy/setup.bash

ros2 run mavros mavros_node \
  --ros-args \
  -p 'fcu_url:=udp://0.0.0.0:14551@' \
  -p system_id:=255 \
  -p component_id:=191 \
  -p target_system_id:=1 \
  -p target_component_id:=1

2. ADIM DOĞRULA

source /opt/ros/jazzy/setup.bash

ros2 topic echo /mavros/state --once


3. ADIM LAUNCH ET

source /opt/ros/jazzy/setup.bash
source ~/rov_ws/install/setup.bash

ros2 launch rov_autonomy rov_teleop.launch.py


arm from terminal

ros2 service call /mavros/cmd/arming mavros_msgs/srv/CommandBool "{value: true}"

disarm

ros2 service call /mavros/cmd/arming mavros_msgs/srv/CommandBool "{value: false}"


DEĞİŞİKLİK YAPARSAN EĞER BUİLD ETMEYİ UNUTMA;


cd ~/rov_ws

source /opt/ros/jazzy/setup.bash

colcon build --packages-select rov_autonomy --symlink-install

source install/setup.bash

```
