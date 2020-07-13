include_directories(
  ${SOURCE_DIR}
  ${GTEST_INCLUDE_DIR}
)

file(GLOB_RECURSE test_sources "*.cpp")

add_executable(test${PROJECT_NAME}
  ${test_sources}
)

target_link_libraries(test${PROJECT_NAME}
  lib${PROJECT_NAME}
  ${GTEST_LIB_DIR}/libgtest.a
  pthread
)

install(TARGETS test${PROJECT_NAME} DESTINATION ${INSTALL_BIN_DIR})
