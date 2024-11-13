# micro_ROS + Ubuntu 22 + Zephyr - Qemu Emulator

Step 1.
> ကဲ ပထမဦးဆုံး ကွာ Qemu Emulator နဲ့ RTOS ပေါင်းပြီး Micro ROS Client (သို့မဟုတ်) DDS Client တစ်ခုပြုလုပ်ရန်။ 

Step 2. 
> Ubuntu 22 ပေါ်မှာ ros2 တင်၊ micro_ros ကိုထပ်ပြီး build လုပ်၊ ပြီး micro_ros_agent သို့မဟုတ် DDS Agent တစ်ခုပြုလုပ်ပါမယ်။

Step 3. 
> ပြီးမှ ခုနက Ubuntu 22 ရဲ့ QEMU ပေါ်မှာ RUN ထားတဲ့ RTOS က DDS Client (သို့မဟုတ်) Micro ROS Client အနေနဲ့ Micro ROS Agent ကိုလာချိတ်ဆက်မှာဖြစ်ပါတယ်။ 

### NOTE 
> Data Distributed System ( DDS ) ကို ROS ကယူသုံးထားတာဖြစ်လို့ ဒီနေရာမှာ Micro_ROS Client နှင့် Micro_ROS Agent လို့ပဲခေါ်တော့မယ်။ stm32.md ဆိုတဲ့ file မှာတော့ DDS-XRCE ကိုသုံးပြီး stm32 chip ပေါ်မှာ RUN ထားတဲ့ steps တွေဝင်ကြည့်နိုင်ပါတယ်။
##
> cd ~/microros_ws

> ros2 run micro_ros_setup create_agent_ws.sh

> colcon build
#### ပြီးတော့ Agent စထောင်လိုက်
##### UDP Localhost အမျိုးအစား
> ros2 run micro_ros_agent micro_ros_agent udp4 --port 8888
##
##### Serial Port အမျိုးအစား
>  ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyACM0

cd ~/microros_ws
colcon build
source install/local_setup.bash

cd ~/microros_ws/src/uros/micro-ROS-demos/rclc/ping_pong
./build/ping_pong/ping_pong

စမ်းလို့မရသေး။ ရခါနီး

##
https://risc-v-getting-started-guide.readthedocs.io/en/latest/getting-zephyr.html

> အထက်ပါ လင့်ကနေ zephyr sdk သွင်းပါ။

1. Zephyr SDK Instllation.
2. Micro-ROS Setup
3. Initialize Zephyr Project

=-=-=-=-=-=--
#### Initialize Zephyr Project

git clone https://github.com/zephyrproject-rtos/zephyr.git ~/workspace/zephyrproject/zephyr

cd ~/workspace/zephyrproject
west init -l zephyr

west update
west zephyr-export


=-=-=-=-=-=-=-=-=-

#### Micro ROS Setup

git clone -b humble https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup


> source /opt/ros/humble/setup.bash

> rosdep update
rosdep install --from-paths src --ignore-src -y

> colcon build

> source install/local_setup.bash


=-=-=-=-=-=-=-=-=-

### After Micro ROS Setup
1. Creating firmware for zephyr platform host

> export ZEPHYR_SDK_INSTALL_DIR=~/zephyr-sdk

> export ZEPHYR_BASE=~/zephyrproject/zephyr

> ros2 run micro_ros_setup create_firmware_ws.sh zephyr host
