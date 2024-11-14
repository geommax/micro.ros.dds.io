# Zephyr RTOS + MICRO-ROS + STM32 

> STLink For Ubuntu

https://github.com/stlink-org/stlink/releases

> Application Development Manual

https://docs.zephyrproject.org/latest/develop/application/index.html#build-an-application

> creating zephyr workspace for stm32f4 disc1 instruction

https://docs.zephyrproject.org/latest/boards/st/stm32f4_disco/doc/index.html

> Usage of gdb and stlink release 

https://github.com/stlink-org/stlink/blob/testing/doc/tutorial.md

## Integration of MICRO-ROS to STM32F407

> ros2 run micro_ros_setup create_firmware_ws.sh zephyr stm32f4_disco



Integrating **micro-ROS** with your STM32F407VG DISC1 board using Zephyr and FreeRTOS requires several steps, as micro-ROS relies on the **ROS 2** ecosystem to bring ROS 2 functionality to microcontrollers. Here’s how to get started:

### 1. Install the micro-ROS CLI Tool

To facilitate integration, the **micro-ROS CLI tool** is essential. It helps with generating necessary files and configuring the workspace.

1. **Install the micro-ROS CLI tool** using `pip`:
   ```bash
   pip install micro-ros-agent
   ```

2. **Install the micro-ROS build system**:
   You’ll need to clone the micro-ROS setup:
   ```bash
   mkdir -p ~/micro_ros_ws/src
   cd ~/micro_ros_ws
   git clone -b humble https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup
   colcon build
   ```

3. **Source the micro-ROS environment**:
   Once the build completes, source the environment:
   ```bash
   source install/local_setup.bash
   ```

### 2. Configure the STM32 Board for micro-ROS

Since you’re working with an STM32F4-based board, you need to use the **Zephyr RTOS** for micro-ROS, as it provides support for STM32 MCUs.

1. **Create a micro-ROS firmware workspace**:
   In the `~/micro_ros_ws` directory, use the micro-ROS CLI to create a new firmware workspace for Zephyr:
   ```bash
   ros2 run micro_ros_setup create_firmware_ws.sh zephyr stm32f4_disco
   ```

2. **Configure the Firmware**:
   Enter the firmware directory and configure it for the STM32F407VG board:
   ```bash
   cd firmware/mcu_ws
   ros2 run micro_ros_setup configure_firmware.sh zephyr
   ```

3. **Customize micro-ROS App**:
   micro-ROS uses a `app` folder where you can write custom ROS 2 nodes. To test basic functionality, you can use one of the pre-defined micro-ROS applications. For example, to set up a simple publisher:
   ```bash
   ros2 run micro_ros_setup create_firmware_ws.sh zephyr
   ```

### 3. Build and Flash micro-ROS Firmware

1. **Build the Firmware**:
   After configuration, navigate back to `firmware/mcu_ws` and build the firmware:
   ```bash
   ros2 run micro_ros_setup build_firmware.sh
   ```

2. **Flash the Firmware**:
   Use the `west` tool or STM32CubeProgrammer to flash the generated firmware:
   ```bash
   west flash
   ```

### 4. Set Up the micro-ROS Agent

The micro-ROS Agent acts as a bridge between the microcontroller (running micro-ROS) and the ROS 2 network. This agent should run on your host computer:

1. **Start the micro-ROS Agent**:
   In a terminal, start the micro-ROS agent to bridge communication between the microcontroller and ROS 2:
   ```bash
   ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyUSB0 -b 115200
   ```
   Replace `/dev/ttyUSB0` with the correct port for your STM32 board’s UART connection.

### 5. Test micro-ROS Communication

With the agent running, you can now communicate with your micro-ROS nodes:

1. **Monitor Messages**:
   Open another terminal and monitor the published messages:
   ```bash
   ros2 topic echo /micro_ros_telemetry_topic
   ```

If you see data flowing, then micro-ROS is successfully integrated with your STM32 board! You can extend this by writing custom micro-ROS applications and deploying more complex ROS 2 nodes. Let me know if you encounter any specific issues along the way!