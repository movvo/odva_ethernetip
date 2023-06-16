cmake_minimum_required(VERSION 3.5)
project(odva_ethernetip)

find_package(ament_cmake REQUIRED)

find_package(console_bridge REQUIRED)
find_package(Boost 1.47 REQUIRED COMPONENTS system)

include_directories(
  include
  ${Boost_INCLUDE_DIRS}
  ${console_bridge_INCLUDE_DIRS}
)

## Declare a cpp library for just Ethernet/IP generic stuff
add_library(${PROJECT_NAME}
  src/connection.cpp
  src/copy_serializable.cpp
  src/cpf_item.cpp
  src/cpf_packet.cpp
  src/encap_header.cpp
  src/encap_packet.cpp
  src/identity_item_data.cpp
  src/io_scanner.cpp
  src/message_router_response.cpp
  src/path.cpp
  src/rr_data.cpp
  src/session.cpp
)

target_link_libraries(${PROJECT_NAME}
  ${Boost_LIBRARIES}
  ${console_bridge_LIBRARIES}
)

## Mark executables and libraries for installation

# target_include_directories(${PROJECT_NAME}
#   PUBLIC
#     $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#     $<INSTALL_INTERFACE:include>)

# ament_export_targets(export_${PROJECT_NAME} HAS_LIBRARY_TARGET)

# install(
#   TARGETS ${PROJECT_NAME}
#   EXPORT export_${PROJECT_NAME}
#   LIBRARY DESTINATION lib
#   ARCHIVE DESTINATION lib
#   RUNTIME DESTINATION bin
#   INCLUDES DESTINATION include
# )

install(
  DIRECTORY include
  DESTINATION include
)

ament_package()

# if (CATKIN_ENABLE_TESTING)
#   catkin_add_gtest(${PROJECT_NAME}-test
#     test/serialization/buffer_writer_test.cpp
#     test/serialization/buffer_reader_test.cpp
#     test/serialization/stream_writer_test.cpp
#     test/serialization/stream_reader_test.cpp
#     test/serialization/serializable_buffer_test.cpp
#     test/serialization/serializable_primitive_test.cpp
#     test/test_socket_test.cpp
#     test/encap_header_test.cpp
#     test/encap_packet_test.cpp
#     test/cpf_item_test.cpp
#     test/cpf_packet_test.cpp
#     test/sequenced_address_item_test.cpp
#     test/identity_item_data_test.cpp
#     test/path_test.cpp
#     test/rr_data_test.cpp
#     test/message_router_request_test.cpp
#     test/message_router_response_test.cpp
#     test/rr_data_request_test.cpp
#     test/rr_data_response_test.cpp
#     test/forward_open_request_test.cpp
#     test/forward_open_success_test.cpp
#     test/forward_close_request_test.cpp
#     test/forward_close_success_test.cpp
#     test/session_test.cpp
#     test/test_main.cpp
#   )
#   target_link_libraries(${PROJECT_NAME}-test ${Boost_LIBRARIES} ${PROJECT_NAME})
# endif()

