set_directory_properties(PROPERTIES LABEL testmesh )
foreach(TEST entity mesh regiontree mesh_codim1 kdtree P1mesh meshmarker updatemarker partitioner_metis elementswithmarkedfaces)

  if(TEST MATCHES partitioner_metis)
      if(FEELPP_HAS_METIS)
          feelpp_add_test( ${TEST} )
      endif()
  else()
      feelpp_add_test( ${TEST} )
  endif()

endforeach()

feelpp_add_test( concatenate SRCS test_concatenate.cpp CFG test_concatenate.cfg GEO test_concatenate.geo )
feelpp_add_test( submesh1d SRCS test_submesh1d.cpp CFG test_submesh1d.cfg GEO test_submesh1d.geo )

# add_custom_target(check COMMAND ${CMAKE_CTEST_COMMAND} DEPENDS ${TESTS} )
