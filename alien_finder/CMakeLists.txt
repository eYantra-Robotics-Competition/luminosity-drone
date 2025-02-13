cmake_minimum_required(VERSION 3.8)
project(alien_finder)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclpy REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(loc_msg REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

install(
  DIRECTORY
    src
    scripts
    launch
  DESTINATION
    share/${PROJECT_NAME}/
)

install(PROGRAMS
  src/mini_core
  src/nano_core
  src/micro_core
  src/big_core
  src/spawner 
  src/spawner_bonus
  scripts/alien_finder.py
  scripts/species_seeker.py
  scripts/Task_6_bonus.py
  scripts/Task_6.py
  DESTINATION lib/${PROJECT_NAME}
)


ament_package()
