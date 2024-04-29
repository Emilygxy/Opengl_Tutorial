cmake_minimum_required (VERSION 3.8)
project (T2_Matrix)
include_directories(${PROJECT_SOURCE_DIR}/include)
link_directories(lib)

#find_package(OpenGL REQUIRED)

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
file(GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)

#生成可执行程序
add_executable(T2_Matrix
    ${HEADERS}
    ${SOURCES}
    ${GLFW_GLAD_INCLUDE_DIR}/../src/glad.c
)

#此处添加依赖库
target_link_libraries(T2_Matrix
    ${GLFW_LIB}
	${THIRD_PARTY_LIB}
)