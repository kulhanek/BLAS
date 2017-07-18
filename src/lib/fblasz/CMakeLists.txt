# ==============================================================================
# BLAS CMake File
# ==============================================================================

# objects in library -----------------------------------------------------------
SET(FBLASZ_SRC
        zaxpy.f
        zcopy.f
        zdotc.f
        zdotu.f
        zdrot.f
        zdscal.f
        zgbmv.f
        zgemm.f
        zgemv.f
        zgerc.f
        zgeru.f
        zhbmv.f
        zhemm.f
        zhemv.f
        zher2.f
        zher2k.f
        zher.f
        zherk.f
        zhpmv.f
        zhpr2.f
        zhpr.f
        zrotg.f
        zscal.f
        zswap.f
        zsymm.f
        zsyr2k.f
        zsyrk.f
        ztbmv.f
        ztbsv.f
        ztpmv.f
        ztpsv.f
        ztrmm.f
        ztrmv.f
        ztrsm.f
        ztrsv.f
        dznrm2.f
        dzasum.f
        cgeru.f
        cswap.f
        cgemm.f
        cscal.f
        icamax.f
        izamax.f
        ctrsm.f
        scabs1.f
        dcabs1.f
        )

# create static library --------------------------------------------------------
IF(LIBS_STATIC)
    ADD_LIBRARY(fblasz_static STATIC ${FBLASZ_SRC})
    SET_TARGET_PROPERTIES(fblasz_static PROPERTIES
                            OUTPUT_NAME fblasz
                            CLEAN_DIRECT_OUTPUT 1)
ENDIF(LIBS_STATIC)

# create shared library --------------------------------------------------------
IF(LIBS_SHARED)
    ADD_LIBRARY(fblasz_shared SHARED ${FBLASZ_SRC})
        SET_TARGET_PROPERTIES(fblasz_shared PROPERTIES
                            OUTPUT_NAME fblasz
                            CLEAN_DIRECT_OUTPUT 1
                            VERSION ${BLAS_VERSION})
                            
    ADD_DEPENDENCIES(fblasz_shared fblasd_shared)
    TARGET_LINK_LIBRARIES(fblasz_shared fblasd_shared)

    INSTALL(TARGETS fblasz_shared
            DESTINATION lib)
ENDIF(LIBS_SHARED)

