1. Установить чистую Ubuntu 20.04 lts.
2. Сделать обновление ссылок и обновление пакетов ОС с помощью команд:
  <br>sudo apt update
  <br>sudo apt upgrade
2. Установить Ros Noetic.
3. Установить пакеты catkin tools.
4. Установить mavros:
  <br>sudo apt-get install ros-noetic-mavros ros-noetic-mavros-extras
5. Установка geographiclib:
  <br>wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
  <br>sudo chmod +x ./install_geographiclib_datasets.sh
  <br>sudo ./install_geographiclib_datasets.sh
6. Скачиваем симулятор:
  <br>git clone https://github.com/LeekaiDel/Firmware.git
  <br>sudo bash ~/Firmware/Tools/setup/ubuntu.sh
  <br>sudo apt install python3-packaging
  <br>sudo apt install python3-jinja2
  <br>sudo apt install python3-toml
  <br>sudo apt update
  <br>sudo apt upgrade
7. Building: 
  <br>cd Firmware
  <br>make clean
  <br>DONT_RUN=1 make px4_sitl_default gazebo
8. Затем в директории Firmware прописываем следующие команды:
  <br>source ~/catkin_ws/devel/setup.bash # (optional)
  <br>source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
  <br>export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)
  <br>export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)/Tools/sitl_gazebo
9. Теперь мы можем запустить симулятор командой:
  <br>roslaunch px4 aerobot_third_test.launch
