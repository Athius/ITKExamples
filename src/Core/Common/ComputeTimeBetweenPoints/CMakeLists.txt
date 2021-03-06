cmake_minimum_required(VERSION 3.10.2)

project( ComputeTimeBetweenPoints )

find_package( ITK REQUIRED )
include( ${ITK_USE_FILE} )

add_executable( ComputeTimeBetweenPoints Code.cxx )
target_link_libraries( ComputeTimeBetweenPoints ${ITK_LIBRARIES} )

install( TARGETS ComputeTimeBetweenPoints
  DESTINATION bin/ITKExamples/Core/Common
  COMPONENT Runtime
)

install( FILES Code.cxx CMakeLists.txt
  DESTINATION share/ITKExamples/Code/Core/Common/ComputeTimeBetweenPoints
  COMPONENT Code
)

enable_testing()
add_test( NAME ComputeTimeBetweenPointsTest
  COMMAND ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/ComputeTimeBetweenPoints )

if( ITK_WRAP_PYTHON )
  add_test( NAME ComputeTimeBetweenPointsTestPython
    COMMAND ${PYTHON_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/Code.py )
endif()
