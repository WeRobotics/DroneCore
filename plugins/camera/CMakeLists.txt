add_library(dronecore_camera ${PLUGIN_LIBRARY_TYPE}
    camera.cpp
    camera_impl.cpp
    camera_definition.cpp
)

target_link_libraries(dronecore_camera
    dronecore
    ${TINYXML2_LIBRARY}
    ${CURL_LIBRARY}
)

include_directories(
    ${CURL_INCLUDE_DIRS}
)

install(FILES
    camera.h
    DESTINATION ${dronecore_install_include_dir}
)

install(TARGETS dronecore_camera
    #EXPORT dronecore-targets
    DESTINATION ${dronecore_install_lib_dir}
)

list(APPEND UNIT_TEST_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/camera_definition_test.cpp
)
set(UNIT_TEST_SOURCES ${UNIT_TEST_SOURCES} PARENT_SCOPE)

