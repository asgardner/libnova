cmake_minimum_required(VERSION 3.25)
project("libnova" C)
enable_testing()
add_library(nova SHARED
    src/aberration.c
    src/airmass.c
    src/angular_separation.c
    src/apparent_position.c
    src/asteroid.c
    src/comet.c
    src/dynamical_time.c
    src/earth.c
    src/elliptic_motion.c
    src/heliocentric_time.c
    src/hyperbolic_motion.c
    src/julian_day.c
    src/jupiter.c
    src/lunar.c
    src/mars.c
    src/mercury.c
    src/neptune.c
    src/nutation.c
    src/parabolic_motion.c
    src/parallax.c
    src/pluto.c
    src/precession.c
    src/proper_motion.c
    src/refraction.c
    src/rise_set.c
    src/saturn.c
    src/sidereal_time.c
    src/solar.c
    src/transform.c
    src/uranus.c
    src/utility.c
    src/venus.c
    src/vsop87.c
)
target_include_directories(nova PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_compile_options(nova PUBLIC -D_POSIX_SOURCE -D_DEFAULT_SOURCE)

install(TARGETS nova EXPORT nova DESTINATION lib)
install(DIRECTORY src/libnova DESTINATION include)

add_executable(nova-test lntest/test.c)
target_include_directories(nova-test PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_link_libraries(nova-test nova m)
