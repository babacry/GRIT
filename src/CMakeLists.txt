set(HEADER_LIST "${grit_SOURCE_DIR}/include/json.hpp" "${grit_SOURCE_DIR}/include/loguru.hpp")

add_library(math_functions math_func.cpp math_func.hpp ${HEADER_LIST})

add_library(body body.cpp body.hpp)

add_library(system system.cpp system.hpp)
target_include_directories(system PUBLIC ../include)
target_link_libraries(system PRIVATE math_functions body)

add_executable(simulate simulate.cpp ${HEADER_LIST})
target_include_directories(simulate PUBLIC ../include)
target_link_libraries(simulate PRIVATE math_functions body system)

# enable_testing()