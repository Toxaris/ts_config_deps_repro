# Reproduction for [rules_ts#271](https://github.com/aspect-build/rules_ts/issues/271)

Goal: Have a first-party package with a tsconfig.json extended by other packages
in the monorepo. The shared tsconfig.json itself extends a tsconfig.json from NPM.
Use workers for `ts_project`.

- `a` has the shared tsconfig.json that depends on package from NPM.
- `b` tries to use the tsconfig.json from `a` with workers _enabled_.
- `c` tries to use the tsconfig.json from `a` with workers _disabled_.

Expected behavior: Both `bazel run //b` and `bazel run //c` should work.

Actual behavior: `bazel run //c` works but `bazel run //b` doesn't.

Error message:

```
b/node_modules/a/tsconfig.json(2,14): error TS6053: File '@tsconfig/node18' not found.
```
