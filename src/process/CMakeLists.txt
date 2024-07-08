# src/process/CMakeLists.txt

# 定义子项目名称为process
project(process)

# 添加共享库process，并指定其源文件
add_library(process
  SHARED
  process.cpp
)

# 设置头文件目录，使库能够找到这些目录中的头文件
target_include_directories(process
  PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR} # 当前目录，即src/process
)

# 链接库，将pnc_map库链接到process库中
target_link_libraries(process
  PUBLIC
  pnc_map # 链接pnc_map库
)
