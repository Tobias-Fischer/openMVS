# Add libraries
ADD_SUBDIRECTORY(Common)
ADD_SUBDIRECTORY(Math)
ADD_SUBDIRECTORY(IO)
ADD_SUBDIRECTORY(MVS)

# Optional prefix for the library file names (e.g. "OpenMVS" gives libOpenMVSCommon,
# libOpenMVSMVS, ...): the plain names are generic and can clash with other
# packages' libraries when installing into a shared lib directory
# (see INSTALL_USE_SUBDIR). Target names (and the OpenMVS:: targets) are unchanged.
SET(OpenMVS_LIBRARY_NAME_PREFIX "" CACHE STRING "Prefix for the file names of the OpenMVS libraries")
IF(OpenMVS_LIBRARY_NAME_PREFIX)
	FOREACH(lib Common Math IO MVS)
		SET_TARGET_PROPERTIES(${lib} PROPERTIES OUTPUT_NAME "${OpenMVS_LIBRARY_NAME_PREFIX}${lib}")
	ENDFOREACH()
ENDIF()

# Install
INSTALL(FILES "MVS.h" DESTINATION "${INSTALL_INCLUDE_DIR}")
