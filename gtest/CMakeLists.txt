cmake_minimum_required(VERSION 3.14)
# 'Google_test' is the subproject name
project(gtest LANGUAGES CUDA CXX)

add_executable(run_google_tests
        allTests.cu
        NeuronTest.cu
        LayerTest.cu
        NetTest.cu
        )

enable_testing()

target_link_libraries(run_google_tests PRIVATE CLDL gtest gtest_main)

set(gtest_force_shared_crt ON FORCE)

set_property(
        TARGET
        run_google_tests
        PROPERTY
        CUDA_RESOLVE_DEVICE_SYMBOLS ON)

add_test(Test_all run_google_tests)
