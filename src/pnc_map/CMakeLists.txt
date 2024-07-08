# src/pnc_map/CMakeLists.txt

# 定义子项目名称为pnc_map
project(pnc_map)

# 添加共享库pnc_map，并指定其源文件
add_library(pnc_map
  SHARED
  pnc_map.cpp
)

# 设置头文件目录，使库能够找到这些目录中的头文件
target_include_directories(pnc_map
  PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR} # 当前目录，即src/pnc_map
)
