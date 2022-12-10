# Reproduction for [rules_ts#271](https://github.com/aspect-build/rules_ts/issues/271)

Goal: Have a first-party package with a tsconfig.json extended by other packages
in the monorepo. The shared tsconfig.json itself extends a tsconfig.json from NPM.

Expectation: `bazel run //b` should work.

Note that the corresponding `pnpm` commands work fine:

```bash
bazel run -- @pnpm//:pnpm --dir $PWD install
bazel run -- @pnpm//:pnpm --dir $PWD --recursive run build
bazel run -- @pnpm//:pnpm --dir $PWD --recursive run start
```
