# 设置所需的最低CMake版本为3.29.0，以确保兼容性和功能性
cmake_minimum_required(VERSION 3.29.0)

# 定义项目名称、版本、描述、主页和使用的语言
project(planning
  VERSION 0.0.1
  DESCRIPTION "a demo of cmake planning"
  HOMEPAGE_URL "https://github.com/dk12399/cmake_planning_demo"
  LANGUAGES CXX)

# 设置C++标准为C++17，以便编译器使用C++17标准进行编译
set(CMAKE_CXX_STANDARD 17)

# 设置所有生成的可执行文件的输出目录为项目根目录下的bin文件夹
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# 定义子目录的路径变量
set(Process_Dir ${CMAKE_SOURCE_DIR}/src/process)
set(Pnc_Map_Dir ${CMAKE_SOURCE_DIR}/src/pnc_map)

# 添加子目录，使CMake处理这些子目录中的CMakeLists.txt文件
add_subdirectory(src/pnc_map)
add_subdirectory(src/process)

# 添加可执行文件planning_main，并指定其源文件
add_executable(planning_main src/planning_main.cpp)

# 设置头文件目录，使可执行文件能够找到这些目录中的头文件
target_include_directories(planning_main
  PUBLIC
  ${Process_Dir} # 包含process目录
  ${Pnc_Map_Dir} # 包含pnc_map目录
)

# 链接库，将共享库链接到可执行文件中
target_link_libraries(planning_main
  PUBLIC
  process # 链接process库
  pnc_map # 链接pnc_map库
)
