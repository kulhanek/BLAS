# ==============================================================================
# BLAS CMake File
# ==============================================================================

# include subdirectories -------------------------------------------------------
ADD_SUBDIRECTORY(fblasd)
IF(LIBS_COMPLEX)
    ADD_SUBDIRECTORY(fblasz)
ENDIF(LIBS_COMPLEX)

