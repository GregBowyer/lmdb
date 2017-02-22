cc_library(
    name = 'lmdb',
    srcs = [
        'libraries/liblmdb/mdb.c',
        'libraries/liblmdb/midl.c',
    ],
    hdrs = [
        'libraries/liblmdb/lmdb.h',
        'libraries/liblmdb/midl.h'
    ],
    copts = [
        "-W",
        "-Wall",
        "-Wno-unused-parameter",
        "-Wbad-function-cast",
        "-Wuninitialized",

        "-DMDB_VL32",
    ],
    linkopts = [
        '-lpthread',
    ],
    includes = ['libraries'],
    nocopts = '-O3|-Ofast|-Wno-literal-suffix',
    visibility = ['//visibility:public'],
)

cc_binary(
    name = 'mdb_stat',
    srcs = ['libraries/liblmdb/mdb_stat.c'],
    deps = [':lmdb'],
    visibility = ['//visibility:public'],
)

cc_binary(
    name = 'mdb_copy',
    srcs = ['libraries/liblmdb/mdb_copy.c'],
    deps = [':lmdb'],
    visibility = ['//visibility:public'],
)

cc_binary(
    name = 'mdb_load',
    srcs = ['libraries/liblmdb/mdb_load.c'],
    deps = [':lmdb'],
    visibility = ['//visibility:public'],
)

cc_binary(
    name = 'mdb_dump',
    srcs = ['libraries/liblmdb/mdb_dump.c'],
    deps = [':lmdb'],
    visibility = ['//visibility:public'],
)

filegroup(
    name = 'lmdb_tools',
    srcs = [
        ':mdb_stat',
        ':mdb_copy',
        ':mdb_load',
        ':mdb_dump',
    ],
    visibility = ['//visibility:public'],
)

cc_test(
    name = 'mtest',
    srcs = ['libraries/liblmdb/mtest.c'],
    deps = [':lmdb'],
)

[
    cc_test(
        name = 'mtest%s' % x,
        srcs = ['libraries/liblmdb/mtest%s.c' % x],
        deps = [':lmdb'],
    )
    for x in range(2, 6)
]

#  vim: set et ft=bzl fenc=utf-8 ff=unix sts=4 sw=4 ts=4 :
