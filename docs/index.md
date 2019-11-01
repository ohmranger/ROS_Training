# Welcome to Ros_Training

โปรแกรมสำหรับดาวร์โหลด    [https://github.com/ohmranger/src](https://github.com/ohmranger/src).

## การติดตั้งโปรแกรม ROS_Melodic
1.1 เข้าไปที่เว็บไซต์หลักของ [ROS](https://www.ros.org/) และติดตั้งจากคำสั่งของ ROS หรือเปิด Terminal<iclass="icon-provider-gdrive"></i>`ctrl+alt+T`

    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

    sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654` 

    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
<div class="admonition note">
    <p class="first admonition-title">Note</p>
    <p class="last">
        หากเกิด ERROR ให้ติดตั้งที่ ROS หลัก
    </p>
</div>