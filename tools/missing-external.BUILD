# This file tests external dependency references
load("@rules_cc//cc:defs.bzl", "cc_library")

cc_library(
    name = "external_lib",
    srcs = ["external.cc"],
    hdrs = ["external.h"], 
    deps = [
        "@missing_external_dep//:core",
        "@fake_external_lib//:utils"
    ],
    visibility = ["//visibility:public"]
)

# Test platform-specific dependencies
platform(
    name = "missing_platform",
    constraint_values = [
        "@platforms//os:linux",
        "@platforms//cpu:x86_64"
    ]
)

config_setting(
    name = "use_missing_lib",
    values = {"define": "use_external=true"}
)

cc_library(
    name = "conditional_lib",
    deps = select({
        ":use_missing_lib": ["@missing_conditional_dep//:lib"],
        "//conditions:default": []
    })
)
