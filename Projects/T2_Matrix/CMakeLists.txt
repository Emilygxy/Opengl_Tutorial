cmake_minimum_required(VERSION 3.8)

project(T2_Matrix)

# #收集文件
file(GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/source/*.cpp)
file(GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)

#生成可执行程序
add_executable(T2_Matrix
    ${HEADERS}
    ${SOURCES}
)

target_include_directories(T2_Matrix PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}source/)

target_link_libraries(T2_Matrix PUBLIC TinyRenderer)
set_target_properties(T2_Matrix
	PROPERTIES 
	RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/$<CONFIGURATION>/
)
target_compile_features(T2_Matrix PRIVATE cxx_std_17)