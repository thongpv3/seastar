set(SEASTAR_LIB_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/build/release)

find_package(PkgConfig REQUIRED)
execute_process(COMMAND pkg-config --cflags --libs ${SEASTAR_LIB_LOCATION}/seastar.pc OUTPUT_VARIABLE SEASTAR_LIB)
string(STRIP "${SEASTAR_LIB}" SEASTAR_LIB)
#add library
add_library(seastar INTERFACE)
target_link_libraries(seastar INTERFACE ${SEASTAR_LIB})
target_include_directories(seastar INTERFACE ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/fmt)