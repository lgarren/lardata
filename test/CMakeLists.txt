# ======================================================================
#
# Testing
#
# ======================================================================

include(CetTest)
cet_enable_asserts()


add_subdirectory( RecoObjects )
add_subdirectory( Utilities )
add_subdirectory( DetectorInfo )
add_subdirectory( DetectorInfoServices )
add_subdirectory( ArtDataHelper )
add_subdirectory( RecoBaseProxy )

# various integration tests

# these tests run a FCL file and fail only if lar exits with a bad exit code;
# they are fast and always run.
# FCL files need to be copied to the test area (DATAFILES directive) since they
# are not installed.
# OPTIONAL_GROUPS is set to execute the test in the "BROKEN" test suite;
# that is because this test is currently failing for MicroBooNE
cet_test(donothing HANDBUILT
  DATAFILES test_donothing.fcl
  TEST_EXEC lar
  TEST_ARGS --rethrow-all --config ./test_donothing.fcl
)


