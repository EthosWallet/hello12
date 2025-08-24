load("@rules_python//python:defs.bzl", "py_library", "py_binary")

# Python targets with missing Bazel dependencies
py_library(
    name = "workspace_lib",
    srcs = ["lib.py"],
    deps = [
        "@missing_python_rules//:core",
        "@fake_py_lib//:utils"
    ]
)

py_binary(
    name = "workspace_app",
    srcs = ["app.py"],
    main = "app.py", 
    deps = [
        ":workspace_lib",
        "@missing_workspace_dep//:main"
    ]
)

# Test workspace-specific missing refs
filegroup(
    name = "workspace_configs",
    srcs = [
        "//missing-workspace-configs:all",
        "//nonexistent-workspace-path:configs"
    ]
)
