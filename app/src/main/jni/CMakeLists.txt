project(ncnnyolov7)

cmake_minimum_required(VERSION 3.10)

include_directories(/home/sasha/Android/OpenCV-android-sdk/sdk/native/jni/include)
add_library( lib_opencv SHARED IMPORTED )
set_target_properties(lib_opencv PROPERTIES IMPORTED_LOCATION /home/sasha/Android/OpenCV-android-sdk/sdk/native/libs/${ANDROID_ABI}/libopencv_java4.so)

#set(OpenCV_DIR /home/sasha/Android/OpenCV-android-sdk/sdk/native/jni)
#find_package(OpenCV REQUIRED core imgproc)

set(ncnn_DIR /home/sasha/Android/ncnn-20240102-android-vulkan/${ANDROID_ABI}/lib/cmake/ncnn)
find_package(ncnn REQUIRED)

add_library(ncnnyolov7 SHARED yoloncnn.cpp yolo.cpp ndkcamera.cpp)

target_link_libraries(ncnnyolov7 ncnn lib_opencv camera2ndk mediandk)
