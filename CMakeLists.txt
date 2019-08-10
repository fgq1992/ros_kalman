cmake_minimum_required(VERSION 2.8.3)
project(ros_kalman)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++11")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall -g")

option(KALMAN_BUILD_EXAMPLES "Build the Kalman examples" ON)

find_package(catkin REQUIRED
    roscpp
    std_msgs   
)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

find_package(Eigen3)

include_directories(
    "include"
    ${catkin_INCLUDE_DIRS}
    ${Eigen3_INCLUDE_DIR}
)

catkin_package()

# set(HEADERS
#     # Base
#     include/kalman/KalmanFilterBase.hpp
#     include/kalman/StandardBase.hpp
#     include/kalman/SquareRootBase.hpp
#     include/kalman/StandardFilterBase.hpp
#     include/kalman/SquareRootFilterBase.hpp

#     # EKF
#     include/kalman/ExtendedKalmanFilter.hpp
#     include/kalman/SquareRootExtendedKalmanFilter.hpp

#     # UKF
#     include/kalman/UnscentedKalmanFilterBase.hpp
#     include/kalman/UnscentedKalmanFilter.hpp
#     include/kalman/SquareRootUnscentedKalmanFilter.hpp

#     # Models
#     include/kalman/MeasurementModel.hpp
#     include/kalman/SystemModel.hpp
#     include/kalman/LinearizedMeasurementModel.hpp
#     include/kalman/LinearizedSystemModel.hpp

#     # Utils
#     include/kalman/Matrix.hpp
#     include/kalman/Types.hpp
# )

if(KALMAN_BUILD_EXAMPLES)
    add_executable(example_robot1 src/Robot1/main.cpp)
endif()

# target_link_libraries(kalman
#     ${catkin_LIBRARIES}
#     )
