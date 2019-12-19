workspace(
    name = "rules_typescript_proto",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "ad4be2c6f40f5af70c7edf294955f9d9a0222c8e2756109731b25f79ea2ccea0",
    urls = [
        "https://github.com/bazelbuild/rules_nodejs/releases/download/0.38.3/rules_nodejs-0.38.3.tar.gz",
    ],
)

http_archive(
    name = "com_github_grpc_grpc",
    sha256 = "950348037825ce013606f5b5b4291fc1d32f79e3c0437747af41813743aa5db8",
    strip_prefix = "grpc-3990d9ce9e796abed897517994b3c93598b9525a",
    urls = [
        "https://github.com/grpc/grpc/archive/3990d9ce9e796abed897517994b3c93598b9525a.tar.gz",
    ],
)

http_archive(
    name = "io_grpc_grpc_java",
    sha256 = "3124f24ed13c5fc26115f9798676902c145cc22f290f0bc4773bd67348f9c0df",
    strip_prefix = "grpc-java-0c4fc64bf2133d7cde8383ca924a8f518e44d8a8",
    urls = [
        "https://github.com/grpc/grpc-java/archive/0c4fc64bf2133d7cde8383ca924a8f518e44d8a8.tar.gz",
    ],
)

http_archive(
    name = "rules_jvm_external",
    sha256 = "02e33287aa6fa129be0a3569ddba0c84ef8eb8b1e5f6f5348373bee559447642",
    strip_prefix = "rules_jvm_external-05ba43aa5b671269cf0dfe2f91ec8f26dcea998e",
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/05ba43aa5b671269cf0dfe2f91ec8f26dcea998e.tar.gz",
)

http_archive(
    name = "rules_proto",
    sha256 = "4d421d51f9ecfe9bf96ab23b55c6f2b809cbaf0eea24952683e397decfbd0dd0",
    strip_prefix = "rules_proto-f6b8d89b90a7956f6782a4a3609b2f0eee3ce965",
    urls = [
        "https://github.com/bazelbuild/rules_proto/archive/f6b8d89b90a7956f6782a4a3609b2f0eee3ce965.tar.gz",
    ],
)

http_archive(
    name = "io_bazel_rules_webtesting",
    sha256 = "ad4be2c6f40f5af70c7edf294955f9d9a0222c8e2756109731b25f79ea2ccea0",
    urls = [
        "https://github.com/bazelbuild/rules_nodejs/releases/download/0.38.3/rules_nodejs-0.38.3.tar.gz",
    ],
)

###################################################################################################

load("@rules_jvm_external//:defs.bzl", "maven_install")
load("@io_bazel_rules_webtesting//web:java_repositories.bzl", "RULES_WEBTESTING_ARTIFACTS")

maven_install(
    artifacts = [
        "com.google.truth:truth:0.42",
        "com.google.truth.extensions:truth-java8-extension:0.42",
        "io.netty:netty-tcnative-boringssl-static:2.0.25.Final",
        "junit:junit:4.13-beta-1",
        "net.bytebuddy:byte-buddy:1.8.22",
        "org.seleniumhq.selenium:selenium-api:3.141.59",
        "org.seleniumhq.selenium:selenium-remote-driver:3.141.59",
        "org.seleniumhq.selenium:selenium-support:3.141.59",
    ] + RULES_WEBTESTING_ARTIFACTS,
    generate_compat_repositories = True,
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

load("@maven//:compat.bzl", "compat_repositories")

compat_repositories()

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

protobuf_deps()

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")

grpc_deps()

load("@io_grpc_grpc_java//:repositories.bzl", "grpc_java_repositories")

grpc_java_repositories()

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

load("@npm//:install_bazel_dependencies.bzl", "install_bazel_dependencies")

install_bazel_dependencies()

load("@npm_bazel_karma//:package.bzl", "npm_bazel_karma_dependencies")

npm_bazel_karma_dependencies()

load("@io_bazel_rules_webtesting//web:repositories.bzl", "web_test_repositories")

web_test_repositories()

load("@io_bazel_rules_webtesting//web/versioned:browsers-0.3.2.bzl", "browser_repositories")

browser_repositories(chromium = True)

load("@npm_bazel_typescript//:index.bzl", "ts_setup_workspace")

ts_setup_workspace()

load("@rules_typescript_proto//:index.bzl", "rules_typescript_proto_dependencies")

rules_typescript_proto_dependencies()
