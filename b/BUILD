load("@npm//:defs.bzl", "npm_link_all_packages")
load("@aspect_rules_js//js:defs.bzl", "js_binary")
load("@aspect_rules_ts//ts:defs.bzl", "ts_config", "ts_project")

npm_link_all_packages()

ts_config(
    name = "tsconfig",
    src = "tsconfig.json",
    deps = [
        ":node_modules/a",
    ],
)

ts_project(
    name = "tsproject",
    srcs = [
        "index.ts",
    ],
    # this does not work :(
    supports_workers = True,
    tsconfig = ":tsconfig",
    deps = [
        ":node_modules/@types/node",
    ],
)

js_binary(
    name = "b",
    data = [
        ":tsproject",
    ],
    entry_point = "index.js",
    visibility = [
        "//visibility:public",
    ],
)
