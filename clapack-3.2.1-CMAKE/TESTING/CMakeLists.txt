if(MSVC_VERSION)
#  string(REPLACE "/STACK:10000000" "/STACK:900000000000000000"
#    CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS}")
  string(REGEX REPLACE "(.*)/STACK:(.*) (.*)" "\\1/STACK:900000000000000000 \\3"
    CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS}")
endif()
add_subdirectory(MATGEN)
add_subdirectory(LIN)
add_subdirectory(EIG)
macro(add_lapack_test output input target)
  set(TEST_INPUT "${CLAPACK_SOURCE_DIR}/TESTING/${input}")
  set(TEST_OUTPUT "${CLAPACK_BINARY_DIR}/TESTING/${output}")
  set_target_properties(${target} PROPERTIES COMPILE_FLAGS ${F2C_FAIL_FLAGS})
  get_target_property(TEST_LOC ${target} LOCATION)
  string(REPLACE "." "_" input_name ${input})
  set(testName "${target}_${input_name}")
  if(EXISTS "${TEST_INPUT}")
    add_test(${testName} "${CMAKE_COMMAND}"
      -DTEST=${TEST_LOC}
      -DINPUT=${TEST_INPUT} 
      -DOUTPUT=${TEST_OUTPUT} 
      -DINTDIR=${CMAKE_CFG_INTDIR}
      -P "${CLAPACK_SOURCE_DIR}/TESTING/runtest.cmake")
  endif()
endmacro(add_lapack_test)

add_lapack_test(stest.out stest.in xlintsts)

add_lapack_test(ctest.out ctest.in xlintstc)
#
# ======== DOUBLE LIN TESTS ===========================

add_lapack_test(dtest.out dtest.in xlintstd)

#
# ======== COMPLEX16 LIN TESTS ========================

add_lapack_test(ztest.out ztest.in xlintstz)

#
# ======== SINGLE-DOUBLE PROTO LIN TESTS ==============

add_lapack_test(dstest.out dstest.in xlintstds)

#
# ======== COMPLEX-COMPLEX16 LIN TESTS ========================

add_lapack_test(zctest.out zctest.in xlintstzc)

#
# ======== SINGLE RFP LIN TESTS ========================

add_lapack_test(stest_rfp.out stest_rfp.in xlintstrfs)

#
# ======== COMPLEX16 RFP LIN TESTS ========================

add_lapack_test(dtest_rfp.out dtest_rfp.in xlintstrfd)

#
# ======== COMPLEX16 RFP LIN TESTS ========================

add_lapack_test(ctest_rfp.out ctest_rfp.in xlintstrfc)

#
# ======== COMPLEX16 RFP LIN TESTS ========================

add_lapack_test(ztest_rfp.out ztest_rfp.in xlintstrfz)

#
#
# ======== SINGLE EIG TESTS ===========================
#

add_lapack_test(snep.out nep.in xeigtsts)


add_lapack_test(ssep.out sep.in xeigtsts)


add_lapack_test(ssvd.out svd.in xeigtsts)


add_lapack_test(sec.out sec.in xeigtsts)


add_lapack_test(sed.out sed.in xeigtsts)


add_lapack_test(sgg.out sgg.in xeigtsts)


add_lapack_test(sgd.out sgd.in xeigtsts)


add_lapack_test(ssb.out ssb.in xeigtsts)


add_lapack_test(ssg.out ssg.in xeigtsts)


add_lapack_test(sbal.out sbal.in xeigtsts)


add_lapack_test(sbak.out sbak.in xeigtsts)


add_lapack_test(sgbal.out sgbal.in xeigtsts)


add_lapack_test(sgbak.out sgbak.in xeigtsts)


add_lapack_test(sbb.out sbb.in xeigtsts)


add_lapack_test(sglm.out glm.in xeigtsts)


add_lapack_test(sgqr.out gqr.in xeigtsts)


add_lapack_test(sgsv.out gsv.in xeigtsts)


add_lapack_test(slse.out lse.in xeigtsts)

#
# ======== COMPLEX EIG TESTS ===========================

add_lapack_test(cnep.out nep.in xeigtstc)


add_lapack_test(csep.out sep.in xeigtstc)


add_lapack_test(csvd.out svd.in xeigtstc)


add_lapack_test(cec.out cec.in xeigtstc)


add_lapack_test(ced.out ced.in xeigtstc)


add_lapack_test(cgg.out cgg.in xeigtstc)


add_lapack_test(cgd.out cgd.in xeigtstc)


add_lapack_test(csb.out csb.in xeigtstc)


add_lapack_test(csg.out csg.in xeigtstc)


add_lapack_test(cbal.out cbal.in xeigtstc)


add_lapack_test(cbak.out cbak.in xeigtstc)


add_lapack_test(cgbal.out cgbal.in xeigtstc)


add_lapack_test(cgbak.out cgbak.in xeigtstc)


add_lapack_test(cbb.out cbb.in xeigtstc)


add_lapack_test(cglm.out glm.in xeigtstc)


add_lapack_test(cgqr.out gqr.in xeigtstc)


add_lapack_test(cgsv.out gsv.in xeigtstc)


add_lapack_test(clse.out lse.in xeigtstc)

#
# ======== DOUBLE EIG TESTS ===========================

add_lapack_test(dnep.out nep.in xeigtstd)


add_lapack_test(dsep.out sep.in xeigtstd)


add_lapack_test(dsvd.out svd.in xeigtstd)


add_lapack_test(dec.out dec.in xeigtstd)


add_lapack_test(ded.out ded.in xeigtstd)


add_lapack_test(dgg.out dgg.in xeigtstd)


add_lapack_test(dgd.out dgd.in xeigtstd)


add_lapack_test(dsb.out dsb.in xeigtstd)


add_lapack_test(dsg.out dsg.in xeigtstd)


add_lapack_test(dbal.out dbal.in xeigtstd)


add_lapack_test(dbak.out dbak.in xeigtstd)


add_lapack_test(dgbal.out dgbal.in xeigtstd)


add_lapack_test(dgbak.out dgbak.in xeigtstd)


add_lapack_test(dbb.out dbb.in xeigtstd)


add_lapack_test(dglm.out glm.in xeigtstd)


add_lapack_test(dgqr.out gqr.in xeigtstd)


add_lapack_test(dgsv.out gsv.in xeigtstd)


add_lapack_test(dlse.out lse.in xeigtstd)

#
# ======== COMPLEX16 EIG TESTS ===========================

add_lapack_test(znep.out nep.in xeigtstz)


add_lapack_test(zsep.out sep.in xeigtstz)


add_lapack_test(zsvd.out svd.in xeigtstz)


add_lapack_test(zec.out zec.in xeigtstz)


add_lapack_test(zed.out zed.in xeigtstz)


add_lapack_test(zgg.out zgg.in xeigtstz)


add_lapack_test(zgd.out zgd.in xeigtstz)


add_lapack_test(zsb.out zsb.in xeigtstz)


add_lapack_test(zsg.out zsg.in xeigtstz)


add_lapack_test(zbal.out zbal.in xeigtstz)


add_lapack_test(zbak.out zbak.in xeigtstz)


add_lapack_test(zgbal.out zgbal.in xeigtstz)


add_lapack_test(zgbak.out zgbak.in xeigtstz)


add_lapack_test(zbb.out zbb.in xeigtstz)


add_lapack_test(zglm.out glm.in xeigtstz)


add_lapack_test(zgqr.out gqr.in xeigtstz)


add_lapack_test(zgsv.out gsv.in xeigtstz)


add_lapack_test(zlse.out lse.in xeigtstz)

# ==============================================================================

