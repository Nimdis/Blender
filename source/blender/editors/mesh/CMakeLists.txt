# ***** BEGIN GPL LICENSE BLOCK *****
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software Foundation,
# Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
#
# Contributor(s): Jacques Beaurain.
#
# ***** END GPL LICENSE BLOCK *****

set(INC
	../include
	../../blenkernel
	../../blenlib
	../../blenloader
	../../imbuf
	../../makesdna
	../../makesrna
	../../render/extern/include
	../../windowmanager
	../../../../intern/guardedalloc
)

set(INC_SYS
	${GLEW_INCLUDE_PATH}
)

set(SRC
	editface.c
	editmesh.c
	editmesh_add.c
	editmesh_lib.c
	editmesh_loop.c
	editmesh_mods.c
	editmesh_tools.c
	loopcut.c
	mesh_data.c
	mesh_ops.c
	meshtools.c

	mesh_intern.h
)

if(WITH_GAMEENGINE)
	add_definitions(-DWITH_GAMEENGINE)

	list(APPEND INC
		../../../../extern/recastnavigation
	)

	list(APPEND SRC
		mesh_navmesh.c
	)
endif()

blender_add_lib(bf_editor_mesh "${SRC}" "${INC}" "${INC_SYS}")
