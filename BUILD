load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")
load("@missing_rules_test//:defs.bzl", "test_rule")

# Test targets that reference missing dependencies
cc_library(
    name = "example_lib",
    srcs = ["lib.cc"],
    hdrs = ["lib.h"],
    deps = [
        "@com_github_google_protobuf//:protobuf",
        "@missing_dependency_test//:core",
        "@local_lib//:utils",
        "@missing_workspace_lib//:common"
    ],
    visibility = ["//visibility:public"]
)

cc_binary(
    name = "example_binary", 
    srcs = ["main.cc"],
    deps = [
        ":example_lib",
        "@fake_missing_repo//:main",
        "@internal_tools//:helpers"
    ]
)

# Test rule from missing dependency
test_rule(
    name = "dependency_test",
    deps = ["@missing_rules_test//:test_lib"]
)

# Local file references that might be missing
filegroup(
    name = "config_files",
    srcs = glob([
        "configs/*.json",
        "../missing-configs/*.yaml"
    ])
)
