cmake_minimum_required(VERSION 3.10.2)

project(fbclock LANGUAGES C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS ON)
set(CMAKE_POSITION_INDEPENDENT_CODE)

set(SRC_FILES
        src/fbanalogclock.c
        src/file.c
        src/font12.c
        src/font16.c
        src/font20.c
        src/font24.c
        src/font8.c
        src/framebuffer.c
        src/list.c
        src/log.c
        src/main.c
        src/numberformat.c
        src/nvp.c
        src/program.c
        src/program_context.c
        src/props.c
        src/region.c
        src/str.c
        src/usage.c
)
add_executable(fbclock ${SRC_FILES})

target_include_directories(fbclock PRIVATE src)

target_compile_definitions(fbclock PRIVATE
        -DNAME=\"${PROJECT_NAME}\"
        -DVERSION=\"1.0b\"
)

target_link_libraries(fbclock PRIVATE -lm)

install(TARGETS fbclock DESTINATION bin)