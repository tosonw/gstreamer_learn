# gstreamer_learn
我用来学习GStreamer的程序，内部有多个demo，只依赖GStreamer，可以自己编译并运行、调试和学习。

依赖：GStreamer
```shell
sudo apt install \
    libssl1.0.0 \
    libgstreamer1.0-0 \
    gstreamer1.0-tools \
    gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-bad \
    gstreamer1.0-plugins-ugly \
    gstreamer1.0-libav \
    libgstrtspserver-1.0-0 \
    libjansson4=2.11-1
```

编译：
```shell
mkdir build
cd build
cmake ..
make
```

运行：
```shell
./demo_1_version_
./demo_2_init_
./demo_3_element_fac_
./demo_4_get_element_info_
./demo_5_link_elements_
./demo_6_pads_
./demo_8_helloworld_
./demo_gstreamer_rtsp_
```

