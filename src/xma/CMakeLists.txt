# SPDX-License-Identifier: Apache-2.0
# Copyright (C) 2019-2021 Xilinx, Inc. All rights reserved.
#
option(XMA_VERBOSE "Enable xma verbosity" OFF)

if (XMA_VERBOSE)
  add_compile_options("-DXMA_VERBOSE")
endif()

add_compile_options("-fPIC")
add_compile_options("-Wall" "-Werror")
set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -Wl,-Bsymbolic")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG}")

add_subdirectory(src)

#Install all header files with directory structure
#Don't remove trailing/ in include/
install(DIRECTORY include/
  DESTINATION ${XMA_INSTALL_DIR}/include/xma2
  COMPONENT ${XRT_DEV_COMPONENT}
  PATTERN "include/lib" EXCLUDE
)
