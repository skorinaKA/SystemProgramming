# CMakeList.txt: проект CMake для SystemProgramming; включите исходный код и определения,
# укажите здесь логику для конкретного проекта.
#
cmake_minimum_required (VERSION 3.8)

# Включение горячей перезагрузки для компиляторов MSVC, если поддерживается.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("SystemProgramming")

# Добавьте источник в исполняемый файл этого проекта.
# add_executable (SystemProgramming "SystemProgramming.cpp" "SystemProgramming.h")
add_executable (komppl "komppl.c")
set_target_properties(komppl PROPERTIES
	VS_DEBUGGER_WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}"
	VS_DEBUGGER_COMMAND_ARGUMENTS "examppl.pli")

if(NOT CMAKE_C_COMPILER)
    message(FATAL_ERROR "CMAKE_C_COMPILER is not set.")
endif()

if (CMAKE_VERSION VERSION_GREATER 3.12)
  # set_property(TARGET SystemProgramming PROPERTY CXX_STANDARD 20)
  set_property(TARGET komppl PROPERTY C_STANDARD 11)
endif()

# TODO: Добавьте тесты и целевые объекты, если это необходимо.
