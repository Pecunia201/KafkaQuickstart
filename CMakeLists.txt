cmake_minimum_required (VERSION 3.8)

# Set the project name
project("KafkaQuickstart")

# Add subdirectories for client and server
add_subdirectory(src/client)
add_subdirectory(src/server)