
# Copyright 2017 Proyectos y Sistemas de Mantenimiento SL (eProsima).
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 2.8.12)
if (${CMAKE_VERSION} VERSION_GREATER 3.0)
    cmake_policy(SET CMP0048 NEW)
endif()

project(PublishSubscribeHelloWorldClient C)

add_executable(${PROJECT_NAME} main.c)
target_link_libraries(${PROJECT_NAME} micrortps_client)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION examples/micrortps/${PROJECT_NAME}/${BIN_INSTALL_DIR}
    )

install(DIRECTORY ${PROJECT_SOURCE_DIR}/
    DESTINATION  examples/micrortps/${PROJECT_NAME}
    FILES_MATCHING PATTERN "*.h"
                   PATTERN "*.c"
                   PATTERN "*.idl"
    )

install(FILES ${PROJECT_SOURCE_DIR}/../../test/hello_topic.xml
              ${PROJECT_SOURCE_DIR}/../../test/hello_data_reader_profile.xml
              ${PROJECT_SOURCE_DIR}/../../test/hello_data_writer_profile.xml
    DESTINATION examples/micrortps/${PROJECT_NAME}/${BIN_INSTALL_DIR}
    )
