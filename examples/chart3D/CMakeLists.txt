IF(BOOST_WT_FOUND)

#
# The ADD_EXAMPLE macro (defined in examples/CMakeLists.txt) ensures that
# the example is correctly built for the requested connector. It is equivalent
# to the following two lines:
#   ADD_EXECUTABLE(hello.wt hello.C)
#   TARGET_LINK_LIBRARIES(hello.wt ${EXAMPLES_CONNECTOR})
# except when the ISAPI (for Microsoft IIS) connector is used, where it will
# build a DLL with the proper symbols exported.
#
WT_ADD_EXAMPLE(chart3D.wt
  chart3D.C
  NumericalExample.C
  CategoryExample.C
  Tabs.C
  DataSettings.C
  Models.C
  CsvUtil.C)
IF(TARGET Boost::headers)
  TARGET_LINK_LIBRARIES(chart3D.wt Boost::headers)
ENDIF()

#
# If you have Wt installed somehwere, you should use the
# installed Wt header files for your own Wt projects.
# e.g. INCLUDE_DIRECTORIES(/usr/local/include)
# instead of the following:
#
INCLUDE_DIRECTORIES(${WT_SOURCE_DIR}/src)
ELSE(BOOST_WT_FOUND)
  MESSAGE(STATUS "** Not building chart3D example: requires boost headers.")
ENDIF(BOOST_WT_FOUND)
