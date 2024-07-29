# Set the project name
project(Server)

# Add executables for client
add_executable(server consumer.c)

# Find the installed packages
find_package(PkgConfig REQUIRED)
pkg_check_modules(RDKAFKA REQUIRED rdkafka)
pkg_check_modules(GLIB REQUIRED glib-2.0)

# Manually set include directories
set(RDKAFKA_INCLUDE_DIRS "/usr/include/librdkafka")
set(RDKAFKA_LIBRARIES "/usr/lib/x86_64-linux-gnu/librdkafka.so")

# Include the directories for the found packages
include_directories(${RDKAFKA_INCLUDE_DIRS})
include_directories(${GLIB_INCLUDE_DIRS})

# Link the libraries to the executable
target_link_libraries(server ${RDKAFKA_LIBRARIES} ${GLIB_LIBRARIES})