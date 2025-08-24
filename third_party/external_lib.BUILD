# Build file for external missing library
load("@rules_cc//cc:defs.bzl", "cc_library")

cc_library(
    name = "missing_external",
    srcs = glob(["src/**/*.cc"]),
    hdrs = glob(["include/**/*.h"]),
    includes = ["include"],
    deps = [
        "@missing_dependency_chain//:base",
        "@fake_third_party//:common"
    ],
    visibility = ["//visibility:public"]
)

# Test transitive missing dependencies
cc_library(
    name = "transitive_missing",
    deps = [
        ":missing_external",
        "@deeply_missing_dep//:core"
    ]
)
