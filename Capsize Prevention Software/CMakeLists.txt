set(PROJECT_NAME CapsizePreventionSoftware)

################################################################################
# Source groups
################################################################################
set(no_group_source_files
    "GLSL/MESHES/sky.qm"
    "GLSL/SHADER/createdisplacement.comp"
    "GLSL/SHADER/creategradients.comp"
    "GLSL/SHADER/debugspectra.frag"
    "GLSL/SHADER/fourier_fft.comp"
    "GLSL/SHADER/ocean.frag"
    "GLSL/SHADER/ocean.vert"
    "GLSL/SHADER/screenquad.frag"
    "GLSL/SHADER/screenquad.vert"
    "GLSL/SHADER/simplecolor.frag"
    "GLSL/SHADER/sky.frag"
    "GLSL/SHADER/sky.vert"
    "GLSL/SHADER/updatespectrum.comp"
    "GLSL/Wave_Height_Map.comp"
)
source_group("" FILES ${no_group_source_files})

set(Header_Files
    "Header Files/3Dmath.h"
    "Header Files/application.h"
    "Header Files/Camera.h"
    "Header Files/dds.h"
    "Header Files/geometryutils.h"
    "Header Files/gl4ext.h"
    "Header Files/glextensions.h"
    "Header Files/GUI.hpp"
    "Header Files/orderedarray.hpp"
    "Header Files/spectatorcamera.h"
    "Header Files/terrainquadtree.h"
    "Header Files/win32application.h"
    "imgui/imgui_impl_opengl3_loader.h"
)
source_group("Header Files" FILES ${Header_Files})

set(Source_Files
    "main.cpp"
    "src/3Dmath.cpp"
    "src/application.cpp"
    "src/dds.cpp"
    "src/fft_test.cpp"
    "src/geometryutils.cpp"
    "src/gl4ext.cpp"
    "src/glextensions.cpp"
    "src/spectatorcamera.cpp"
    "src/terrainquadtree.cpp"
    "src/win32application.cpp"
)
source_group("Source Files" FILES ${Source_Files})

set(ALL_FILES
    ${no_group_source_files}
    ${Header_Files}
    ${Source_Files}
)

################################################################################
# Target
################################################################################
add_executable(${PROJECT_NAME} ${ALL_FILES})

use_props(${PROJECT_NAME} "${CMAKE_CONFIGURATION_TYPES}" "${DEFAULT_CXX_PROPS}")
set(ROOT_NAMESPACE CapsizePreventionSoftware)

set_target_properties(${PROJECT_NAME} PROPERTIES
    VS_GLOBAL_KEYWORD "Win32Proj"
)
if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
    set_target_properties(${PROJECT_NAME} PROPERTIES
        INTERPROCEDURAL_OPTIMIZATION_RELEASE "TRUE"
    )
elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
    set_target_properties(${PROJECT_NAME} PROPERTIES
        INTERPROCEDURAL_OPTIMIZATION_RELEASE "TRUE"
    )
endif()
################################################################################
# Include directories
################################################################################
if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
    target_include_directories(${PROJECT_NAME} PUBLIC
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/glew-2.1.0/include;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/stb-master;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/glm;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/Extern/Include/OpenGL"
    )
elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
    target_include_directories(${PROJECT_NAME} PUBLIC
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/GLFW/include;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/glew-2.1.0/include;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/stb-master;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/glm;"
        "${CMAKE_CURRENT_SOURCE_DIR}/../Dependencies/imgui"
    )
endif()

################################################################################
# Compile definitions
################################################################################
if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
    target_compile_definitions(${PROJECT_NAME} PRIVATE
        "GLEW_STATIC;"
        "STB_IMAGE_IMPLEMENTATION;"
        "OPENGL;"
        "_MBCS"
    )
elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
    target_compile_definitions(${PROJECT_NAME} PRIVATE
        "GLEW_STATIC;"
        "STB_IMAGE_IMPLEMENTATION;"
        "UNICODE;"
        "_UNICODE"
    )
endif()

################################################################################
# Compile and link options
################################################################################
if(MSVC)
    if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
        target_compile_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Release>:
                /Oi;
                /Gy
            >
            /permissive-;
            /sdl;
            /W3;
            ${DEFAULT_CXX_DEBUG_INFORMATION_FORMAT};
            ${DEFAULT_CXX_EXCEPTION_HANDLING}
        )
    elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
        target_compile_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Release>:
                /Oi;
                /Gy
            >
            /permissive-;
            /sdl;
            /W3;
            ${DEFAULT_CXX_DEBUG_INFORMATION_FORMAT};
            ${DEFAULT_CXX_EXCEPTION_HANDLING}
        )
    endif()
    if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
        target_link_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Debug>:
                /INCREMENTAL
            >
            $<$<CONFIG:Release>:
                /OPT:REF;
                /OPT:ICF;
                /INCREMENTAL:NO
            >
            /DEBUG;
            /SUBSYSTEM:CONSOLE
        )
    elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
        target_link_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Debug>:
                /INCREMENTAL
            >
            $<$<CONFIG:Release>:
                /OPT:REF;
                /OPT:ICF;
                /INCREMENTAL:NO
            >
            /DEBUG;
            /SUBSYSTEM:CONSOLE
        )
    endif()
endif()

################################################################################
# Dependencies
################################################################################
if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
    set(ADDITIONAL_LIBRARY_DEPENDENCIES
        "glew32s;"
        "opengl32;"
        "kernel32;"
        "user32;"
        "gdi32;"
        "winspool;"
        "comdlg32;"
        "advapi32;"
        "shell32;"
        "ole32;"
        "oleaut32;"
        "uuid;"
        "odbc32;"
        "odbccp32;"
        "glslang;"
        "HLSL;"
        "OGLCompiler;"
        "OSDependent;"
        "d3d9"
    )
elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
    set(ADDITIONAL_LIBRARY_DEPENDENCIES
        "glfw3;"
        "glew32s;"
        "opengl32;"
        "kernel32;"
        "user32;"
        "gdi32;"
        "winspool;"
        "comdlg32;"
        "advapi32;"
        "shell32;"
        "ole32;"
        "oleaut32;"
        "uuid;"
        "odbc32;"
        "odbccp32"
    )
endif()
target_link_libraries(${PROJECT_NAME} PRIVATE "${ADDITIONAL_LIBRARY_DEPENDENCIES}")

if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
    target_link_directories(${PROJECT_NAME} PRIVATE
        "${CMAKE_SOURCE_DIR}/Dependencies/glew-2.1.0/lib/Release/x64;"
        "${CMAKE_SOURCE_DIR}/Dependencies/Extern/Lib/glslang"
    )
elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x86")
    target_link_directories(${PROJECT_NAME} PRIVATE
        "${CMAKE_SOURCE_DIR}/Dependencies/GLFW/lib-vc2019;"
        "${CMAKE_SOURCE_DIR}/Dependencies/glew-2.1.0/lib/Release/x64"
    )
endif()

