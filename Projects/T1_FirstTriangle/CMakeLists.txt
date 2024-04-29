cmake_minimum_required(VERSION 3.8)

project(T1_FirstTriangle)

# #收集文件
file(GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/source/*.cpp)
file(GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)

#生成可执行程序
add_executable(T1_FirstTriangle
    ${HEADERS}
    ${SOURCES}
)

target_include_directories(T1_FirstTriangle PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}source/)

target_link_libraries(T1_FirstTriangle PUBLIC TinyRenderer)
set_target_properties(T1_FirstTriangle
	PROPERTIES 
	RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/$<CONFIGURATION>/
)
target_compile_features(T1_FirstTriangle PRIVATE cxx_std_17)