cmake_minimum_required (VERSION 3.8)

project (TinyRenderer)

include_directories(${PROJECT_SOURCE_DIR}/include)
link_directories(lib)

#find_package(OpenGL REQUIRED)
SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/build/bin)
SET(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/build/bin)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

set(GLFW_GLAD_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/OpenGL/include)
set(GLFW_LIB ${CMAKE_CURRENT_SOURCE_DIR}/OpenGL/lib/glfw3.lib)
set(THIRD_PARTY_LIB 
	${CMAKE_CURRENT_SOURCE_DIR}/thirdParty/glm/lib/glm.lib
	)

set(THIRD_PARTY_INCLUDE_DIR 
	${CMAKE_CURRENT_SOURCE_DIR}/thirdParty/glm/
	)

#添加依赖的头文件
include_directories(
    ${GLFW_GLAD_INCLUDE_DIR}
	${THIRD_PARTY_INCLUDE_DIR}
)

#收集文件
file(GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/source/*.cpp)
file(GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/source/*.c)
file(GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)

# add_library(TinyRenderer SHARED ${SOURCES})  ## dll
add_library(TinyRenderer STATIC ${SOURCES})  ## lib

#生成可执行程序
add_subdirectory(T1_FirstTriangle)
add_subdirectory(T2_Matrix)

#此处添加依赖库
target_link_libraries(TinyRenderer
    ${GLFW_LIB}
	${THIRD_PARTY_LIB}
)

set_target_properties( TinyRenderer
    PROPERTIES
	FOLDER "Libraries"
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/$<CONFIGURATION>/
)

target_compile_features(TinyRenderer PRIVATE cxx_std_17)