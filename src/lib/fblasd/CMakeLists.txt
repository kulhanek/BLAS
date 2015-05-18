# ==============================================================================
# BLAS CMake File
# ==============================================================================

# objects in library -----------------------------------------------------------
SET(FBLASD_SRC
        dasum.f
        daxpy.f
        dcopy.f
        ddot.f
        dgbmv.f
        dgemm.f
        dgemv.f
        dger.f
        dnrm2.f
        drot.f
        drotg.f
        drotm.f
        drotmg.f
        dsbmv.f
        dscal.f
        dsdot.f
        dspmv.f
        dspr2.f
        dspr.f
        dswap.f
        dsymm.f
        dsymv.f
        dsyr2.f
        dsyr2k.f
        dsyr.f
        dsyrk.f
        dtbmv.f
        dtbsv.f
        dtpmv.f
        dtpsv.f
        dtrmm.f
        dtrmv.f
        dtrsm.f
        dtrsv.f
        idamax.f
        lsame.f
        xerbla.f
        )

# create static library --------------------------------------------------------
IF(LIBS_STATIC)
    ADD_LIBRARY(fblasd_static STATIC ${FBLASD_SRC})
    SET_TARGET_PROPERTIES(fblasd_static PROPERTIES
                            OUTPUT_NAME fblasd
                            CLEAN_DIRECT_OUTPUT 1)
ENDIF(LIBS_STATIC)

# create shared library --------------------------------------------------------
IF(LIBS_SHARED)
    ADD_LIBRARY(fblasd_shared SHARED ${FBLASD_SRC})
    SET_TARGET_PROPERTIES(fblasd_shared PROPERTIES
                            OUTPUT_NAME fblasd
                            CLEAN_DIRECT_OUTPUT 1
                            VERSION ${BLAS_VERSION})
    INSTALL(TARGETS fblasd_shared
            DESTINATION lib)
ENDIF(LIBS_SHARED)

