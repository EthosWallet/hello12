workspace(name = "example_workspace")

# Git repository dependencies (potential repo jacking)
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "com_github_google_protobuf",
    remote = "https://github.com/protocolbuffers/protobuf.git",
    tag = "v3.21.0"
)

git_repository(
    name = "fake_missing_repo",
    remote = "https://github.com/nonexistent-org/missing-bazel-lib.git",
    commit = "abc123def456"
)

# HTTP archive dependencies (potential dependency confusion)
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_nodejs",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.8.2/rules_nodejs-5.8.2.tar.gz"],
    sha256 = "f10a3a12894fc3c9bf578ee5a5691769f6805c4be84359681a785a0c12e8d2b6"
)

http_archive(
    name = "missing_dependency_test",
    urls = ["https://example.com/nonexistent-package.tar.gz"],
    sha256 = "fake_sha256_for_testing"
)

# Local repository dependencies (workspace path vulnerabilities)
local_repository(
    name = "local_lib",
    path = "../missing-local-lib"
)

local_repository(
    name = "internal_tools",
    path = "./tools/missing-tools"
)

local_repository(
    name = "shared_utils",
    path = "/usr/local/shared/utils"
)

# Maven dependencies (potential confusion)
load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "com.google.guava:guava:31.1-jre",
        "org.apache.commons:commons-lang3:3.12.0",
        "com.example:missing-artifact:1.0.0",
        "org.nonexistent:fake-lib:2.3.1"
    ],
    repositories = [
        "https://repo1.maven.org/maven2/",
        "https://maven.google.com"
    ]
)

# Archive override (potential confusion)
archive_override(
    module_name = "missing_module",
    urls = ["https://github.com/missing-org/missing-module/archive/v1.0.tar.gz"]
)

# New git repository (enhanced detection)
load("@bazel_tools//tools/build_defs/repo:git.bzl", "new_git_repository")

new_git_repository(
    name = "external_missing_lib",
    remote = "https://github.com/fake-org/external-missing-lib.git",
    tag = "v2.1.0",
    build_file = "@//third_party:external_lib.BUILD"
)
