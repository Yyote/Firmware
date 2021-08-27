1. Установить чистую Ubuntu 20.04 lts.
2. Сделать обновление ссылок и обновление пакетов ОС с помощью команд:
  sudo apt update,
  sudo apt upgrade
2. Установить Ros Noetic
3. Установить пакеты catkin tools
4. Установить mavros
  sudo apt-get install ros-noetic-mavros ros-noetic-mavros-extras
5. Установка geographiclib:
  wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
  sudo chmod +x ./install_geographiclib_datasets.sh
  sudo ./install_geographiclib_datasets.sh
6. Скачиваем симулятор
  git clone https://github.com/LeekaiDel/Firmware.git
7. Building: 
  cd Firmware
  DONT_RUN=1 make px4_sitl_default gazebo
8. Затем в директории Firmware прописываем следующие команды:
  source ~/catkin_ws/devel/setup.bash # (optional)
  source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
  export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)
  export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)/Tools/sitl_gazebo
9. Теперь мы можем запустить симулятор командой:
  roslaunch px4 aerobot_second_test.launch
