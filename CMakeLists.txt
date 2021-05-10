cmake_minimum_required(VERSION 3.16)
project(secp256k1)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_C_STANDARD 11)

set(SECP256K1_HDR
    include/secp256k1.h
    include/secp256k1_preallocated.h
    )

set(SECP256K1_INC
    src/libsecp256k1-config.h
    src/scalar.h
    src/scalar_4x64.h
    src/scalar_8x32.h
    src/scalar_low.h
    src/scalar_impl.h
    src/scalar_4x64_impl.h
    src/scalar_8x32_impl.h
    src/scalar_low_impl.h
    src/group.h
    src/group_impl.h
    src/ecdsa.h
    src/ecdsa_impl.h
    src/eckey.h
    src/eckey_impl.h
    src/ecmult.h
    src/ecmult_impl.h
    src/ecmult_const.h
    src/ecmult_const_impl.h
    src/ecmult_gen.h
    src/ecmult_gen_impl.h
    src/field_10x26.h
    src/field_10x26_impl.h
    src/field_5x52.h
    src/field_5x52_impl.h
    src/field_5x52_int128_impl.h
    src/field_5x52_asm_impl.h
    src/modinv32.h
    src/modinv32_impl.h
    src/modinv64.h
    src/modinv64_impl.h
    src/assumptions.h
    src/util.h
    src/scratch.h
    src/scratch_impl.h
    src/selftest.h
    src/testrand.h
    src/testrand_impl.h
    src/hash.h
    src/hash_impl.h
    src/field.h
    src/field_impl.h
    src/bench.h
    contrib/lax_der_parsing.h
    contrib/lax_der_parsing.c
    contrib/lax_der_privatekey_parsing.h
    contrib/lax_der_privatekey_parsing.c
    )

set(SECP256K1_SRC
    src/secp256k1.c
    )

add_library(secp256k1 STATIC ${SECP256K1_HDR} ${SECP256K1_INC} ${SECP256K1_SRC})
target_compile_definitions(secp256k1 PRIVATE HAVE_CONFIG_H)
target_include_directories(secp256k1 PUBLIC include)
target_include_directories(secp256k1 PRIVATE src)
