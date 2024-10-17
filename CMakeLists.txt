#############################################################################
# weBIGeo
# Copyright (C) 2024 Gerald Kimmersdorfer
# Copyright (C) 2022-2023 Élie Michel and contributors 
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#############################################################################

add_library(imgui STATIC
    # Among the different backends available, we are interested in connecting
    # the GUI to GLFW and WebGPU:
    backends/imgui_impl_wgpu.h
    backends/imgui_impl_wgpu.cpp
    backends/imgui_impl_sdl2.h
    backends/imgui_impl_sdl2.cpp

    # Bonus to add some C++ specific features (the core ImGUi is a C library)
    misc/cpp/imgui_stdlib.h
    misc/cpp/imgui_stdlib.cpp

    # The core ImGui files
    imconfig.h
    imgui.h imgui.cpp
    imgui_draw.cpp
    imgui_internal.h
    imgui_tables.cpp
    imgui_widgets.cpp
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
)

target_include_directories(imgui PUBLIC .)
target_link_libraries(imgui PUBLIC webgpu)