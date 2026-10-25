# bun-python

Bun Python (PyJS) for the Aphrody Bun fork: `buv` (the PyJS/PyTS/PyTSX toolchain
and its LSP, GPU and runtime-artifact tooling), `bun-python-native` (the lazy shared
CPython host `bun_python_host`, its C ABI, patches and WASM build),
`bun-python-toolchain` (pinned toolchain receipts) and `bun-python-conformance`.

Imported from `packages/{buv,bun-python-native,bun-python-toolchain,bun-python-conformance}`
of [aphrody-labs/bun](https://github.com/aphrody-labs/bun), which keeps the earlier history.
Bun OS ([aphrody-labs/bun-os](https://github.com/aphrody-labs/bun-os.git)) mounts it as
`vendor/bun-python`.

## Install and use

`bun:python` and `bun python` are part of the `bun` runtime and load the host library at
run time (`BUN_PYTHON_HOST_LIBRARY`, or one embedded in a compiled executable). UV comes
from the `bun uv` plugin (aphrody-labs/bun-uv).

## Build from source

Mount it in a Bun checkout, which this tree's scripts and the uv plugin expect:

```sh
git -C <bun checkout> submodule update --init --checkout packages/bun-python
cd <bun checkout>/packages/bun-python
cargo build --locked --release -p bun-python-host   # libbun_python_host / bun_python_host.dll
```

`Cargo.lock` was derived from the Bun workspace lockfile.
