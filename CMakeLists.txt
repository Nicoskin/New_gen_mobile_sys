cmake_minimum_required(VERSION 3.10)

# Установите имя проекта
project(Client_Server)

# Создайте исполняемые файлы для сервера и клиента
add_executable(main src/main.c)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/test)


# Свяжите библиотеки с исполняемыми файлами
target_link_libraries(server ${ZMQ_LIBRARIES} ${CZMQ_LIBRARIES})
target_link_libraries(client ${ZMQ_LIBRARIES} ${CZMQ_LIBRARIES})

# Включите директории заголовков
target_include_directories(server PRIVATE 
    ${ZMQ_INCLUDE_DIRS}
    ${CZMQ_INCLUDE_DIRS}
)

target_include_directories(client PRIVATE 
    ${ZMQ_INCLUDE_DIRS}
    ${CZMQ_INCLUDE_DIRS}
)

# Установите стандарт C++
set_target_properties(server PROPERTIES
    CXX_STANDARD 11  
    CXX_STANDARD_REQUIRED ON
)

set_target_properties(client PROPERTIES
    CXX_STANDARD 11  
    CXX_STANDARD_REQUIRED ON
)
