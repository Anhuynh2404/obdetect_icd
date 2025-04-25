cmake_minimum_required(VERSION 3.10)
# Tên project
project(nanodet_demo)
# Đặt tiêu chuẩn C++
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(Torch_DIR "/home/an/an_workplace/ICD/obdetect_icd/demo_libtorch/libtorch/share/cmake/Torch")

# Chỉ định đường dẫn Torch trước khi tìm package
find_package(OpenCV REQUIRED)
find_package(Torch REQUIRED)
# Cờ biên dịch (nếu cần)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${TORCH_CXX_FLAGS}")
# Bao gồm thư viện và header
include_directories(
    ${OpenCV_INCLUDE_DIRS}
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_BINARY_DIR}
)
# Tạo executable
add_executable(nanodet_demo main.cpp nanodet_libtorch.cpp)
# Liên kết thư viện
target_link_libraries(
    nanodet_demo
    ${TORCH_LIBRARIES}
    ${OpenCV_LIBS}
)
# Copy DLLs nếu dùng trên Windows
if (MSVC)
  file(GLOB TORCH_DLLS "${TORCH_INSTALL_PREFIX}/lib/*.dll")
  add_custom_command(TARGET nanodet_demo
                     POST_BUILD
                     COMMAND ${CMAKE_COMMAND} -E copy_if_different
                     ${TORCH_DLLS}
                     $<TARGET_FILE_DIR:nanodet_demo>)
endif (MSVC)
