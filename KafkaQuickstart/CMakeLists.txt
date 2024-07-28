# CMakeList.txt : CMake project for CMakeProject2, include source and define
# project specific logic here.
#

# Add source to this project's executable.
#add_executable(CMakeProject2  "common.c"  "producer.c" "consumer.c")

# Define the producer executable
add_executable(producer "common.c" "producer.c")

# Define the consumer executable
add_executable(consumer "common.c" "consumer.c")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET producer PROPERTY CXX_STANDARD 20)
  set_property(TARGET consumer PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.

# Find the installed packages
find_package(PkgConfig REQUIRED)
pkg_check_modules(RDKAFKA REQUIRED rdkafka)
pkg_check_modules(GLIB REQUIRED glib-2.0)

# Manually set include directories if not found
if(NOT RDKAFKA_INCLUDE_DIRS)
    set(RDKAFKA_INCLUDE_DIRS "/usr/include/librdkafka")
    message(WARNING "RDKAFKA_INCLUDE_DIRS not found, setting manually to ${RDKAFKA_INCLUDE_DIRS}")
endif()

# Manually set library directories if not found
if(NOT RDKAFKA_LIBRARIES)
    set(RDKAFKA_LIBRARIES "/usr/lib/x86_64-linux-gnu/librdkafka.so")
    message(WARNING "RDKAFKA_LIBRARIES not found, setting manually to ${RDKAFKA_LIBRARIES}")
endif()

# Include the directories for the found packages
include_directories(${RDKAFKA_INCLUDE_DIRS})
include_directories(${GLIB_INCLUDE_DIRS})

# Link the libraries to the executable
target_link_libraries(producer ${RDKAFKA_LIBRARIES} ${GLIB_LIBRARIES})
target_link_libraries(consumer ${RDKAFKA_LIBRARIES} ${GLIB_LIBRARIES})