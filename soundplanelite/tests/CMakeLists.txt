set(SOUNDPLANETEST_SRC "soundplanetest.cpp")
include_directories ("${PROJECT_SOURCE_DIR}/soundplanelite")
add_executable(soundplanetest ${SOUNDPLANETEST_SRC})
target_link_libraries (soundplanetest soundplanelite portaudio)
if(CMAKE_COMPILER_IS_GNUCC OR CMAKE_COMPILER_IS_GNUCXX)
  target_link_libraries(soundplanetest atomic)
endif()
if(APPLE)
target_link_libraries(soundplanetest  "-framework CoreServices -framework CoreFoundation -framework IOKit -framework CoreAudio")
elseif(UNIX) 
target_link_libraries(soundplanetest pthread libusb)
endif(APPLE)

set(TOUCHTRACKERTEST_SRC "touchtrackertest.cpp")
include_directories ("${PROJECT_SOURCE_DIR}/soundplanelite")
add_executable(touchtrackertest ${TOUCHTRACKERTEST_SRC})

target_link_libraries (touchtrackertest soundplanelite portaudio)
if(CMAKE_COMPILER_IS_GNUCC OR CMAKE_COMPILER_IS_GNUCXX)
  target_link_libraries(touchtrackertest atomic)
endif()
if(APPLE)
target_link_libraries(touchtrackertest  "-framework CoreServices -framework CoreFoundation -framework IOKit -framework CoreAudio")
elseif(UNIX) 
target_link_libraries(touchtrackertest pthread libusb)
endif(APPLE)
