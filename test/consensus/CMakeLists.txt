SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/my_test_bin)

SET(CMAKE_CXX_FLAGS_DEBUG "-g")

SET(KECCAK_PATH  "${PROJECT_SOURCE_DIR}/core/vendor/KeccakCodePackage")
SET(ED25519_PATH "${PROJECT_SOURCE_DIR}/core/vendor/ed25519")

link_directories(
    ${PROJECT_BINARY_DIR}/lib
    ${ED25519_PATH}/lib
    ${KECCAK_PATH}/bin/generic64
    ${PROJECT_SOURCE_DIR}/core/infra/crypto
    ${AERON_PATH}/cppbuild/Release/lib
)

add_executable(sumeragi_test
    sumeragi_test.cpp
)
target_link_libraries(sumeragi_test
    snappy
    objects
    base64
    signature
    convertor
    sumeragi
    connection_with_grpc
    peer_service_with_json
    pthread
    consensus_event
    transaction
)

add_executable(transaction_test
    transaction_test.cpp
)
target_link_libraries(transaction_test
    snappy
    objects
    base64
    signature
    sumeragi
    commands
    connection_with_grpc
    peer_service_with_json
    pthread
    consensus_event
    transaction
    objects
)