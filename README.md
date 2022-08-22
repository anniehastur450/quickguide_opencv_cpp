Quick environment setup guide on opencv for cpp
===

Command line
---
(Tested on Ubuntu 18)
1. install libopencv-dev
    ```
    sudo apt install libopencv-dev
    ```
2. check pkg-config for opencv: `pkg-config --cflags --libs opencv`

    it should look like this, then you have no issues
    ```
    $ pkg-config --cflags --libs opencv
    -I/usr/include/opencv -lopencv_shape -lopencv_stitching -lopencv_superres -lopencv_videostab -lopencv_aruco -lopencv_bgsegm -lopencv_bioinspired -lopencv_ccalib -lopencv_datasets -lopencv_dpm -lopencv_face -lopencv_freetype -lopencv_fuzzy -lopencv_hdf -lopencv_line_descriptor -lopencv_optflow -lopencv_video -lopencv_plot -lopencv_reg -lopencv_saliency -lopencv_stereo -lopencv_structured_light -lopencv_phase_unwrapping -lopencv_rgbd -lopencv_viz -lopencv_surface_matching -lopencv_text -lopencv_ximgproc -lopencv_calib3d -lopencv_features2d -lopencv_flann -lopencv_xobjdetect -lopencv_objdetect -lopencv_ml -lopencv_xphoto -lopencv_highgui -lopencv_videoio -lopencv_imgcodecs -lopencv_photo -lopencv_imgproc -lopencv_core
    ```
3. compile main.cpp is simple, just run
    ```
    g++ main.cpp -o main `pkg-config --cflags --libs opencv`
    ```
    which produce a executable called `main`,
    then you can run `./main` to execute the program
    ```
    ./main
    ```

Configuration on VSCode
---

### Run / Debug / task.json

task.json support command substitution, thanks to that,
we can include opencv library without typing a lot of args in task.json

1. generate task.json by vscode (make sure the C/C++ extension is installed)

    - Click Run and Debug
    - A `Select a configuration` prompt popped up, choose Detected Task, C/C++: g++ build and debug active file
    - Click Abort when any error messages pop up

2. edit task.json

    - make sure "command" is "g++" or "/usr/bin/g++"
    - add this after the last element of "args"
    ```
        "`pkg-config --cflags --libs opencv`"
    ```

3. now the Run and Debug by vscode should successfully execute the program

### VSCode Intellisense / c_cpp_properties.json


