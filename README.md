# Reproduction for [rules_ts#271](https://github.com/aspect-build/rules_ts/issues/271)

Goal: Have a first-party package with a tsconfig.json extended by other packages
in the monorepo. The shared tsconfig.json itself extends a tsconfig.json from NPM.

Expected behavior: `bazel run //b` should work.

Actual behavior:

```
b/node_modules/a/tsconfig.json(2,14): error TS6053: File '@tsconfig/node18' not found.
```

Note that the corresponding `pnpm` commands work fine:

```bash
bazel run -- @pnpm//:pnpm --dir $PWD install
bazel run -- @pnpm//:pnpm --dir $PWD --recursive run build
bazel run -- @pnpm//:pnpm --dir $PWD --recursive run start
```
