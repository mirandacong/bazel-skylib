load("//lib:unittest.bzl", "TOOLCHAIN_TYPE", "unittest_toolchain")

toolchain_type(
    name = "toolchain_type",
    visibility = ["//visibility:public"],
)

unittest_toolchain(
    name = "cmd",
    failure_templ = """@echo off
echo %s
exit /b 1
""",
    file_ext = ".bat",
    join_on = "\necho ",
    success_templ = "@exit /b 0",
    visibility = ["//visibility:public"],
)

unittest_toolchain(
    name = "bash",
    failure_templ = """#!/bin/sh
cat <<'EOF'
%s
EOF
exit 1
""",
    file_ext = ".sh",
    join_on = "\n",
    success_templ = "#!/bin/sh\nexit 0",
    visibility = ["//visibility:public"],
)

toolchain(
    name = "cmd_toolchain",
    exec_compatible_with = [
        "@bazel_tools//platforms:windows",
    ],
    toolchain = ":cmd",
    toolchain_type = TOOLCHAIN_TYPE,
)

toolchain(
    name = "bash_toolchain",
    toolchain = ":bash",
    toolchain_type = TOOLCHAIN_TYPE,
)
