get_filename_component(CURR_DIR_NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME)

file(GLOB files
	"*.h"
	"*.hpp"
	"*.cpp"
)

add_library("${CURR_DIR_NAME}"  ${files})
