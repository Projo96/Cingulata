cmake_minimum_required(VERSION 3.9)

add_executable(tfhe-trans2-exec transaction.cxx)
target_link_libraries(tfhe-trans2-exec common tfhe_bit_exec)

add_executable(tfhe-trans2-encrypt encrypt.cxx)
target_link_libraries(tfhe-trans2-encrypt common tfhe_bit_exec)

add_executable(tfhe-trans2-decrypt decrypt.cxx)
target_link_libraries(tfhe-trans2-decrypt common tfhe_bit_exec)

add_custom_target(tfhe-trans2
  DEPENDS
    tfhe-keygen
    tfhe-trans2-exec
    tfhe-trans2-encrypt
    tfhe-trans2-decrypt
)

set(APPS_DIR ${CMAKE_BINARY_DIR}/apps)
configure_file("run.sh.in" "run.sh" @ONLY)
