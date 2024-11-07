cd ..

<install rust>

rustup target add wasm32-wasi

cargo build --target wasm32-wasi --release

curl -sSf https://raw.githubusercontent.com/WasmEdge/WasmEdge/master/utils/install.sh | bash

wasmedge --dir .:. target/wasm32-wasi/release/wasmedge_quickjs.wasm example_js/hello.js WasmEdge Runtime

wasmedge --dir .:. target/wasm32-wasi/release/wasmedge_quickjs.wasm test01/fib.js

<take longer than 30s>

```
$ curl https://wasmtime.dev/install.sh -sSf | bash

$ wasmtime --dir . target/wasm32-wasi/release/wasmedge_quickjs.wasm test01/fib.js

Error: failed to run main module `target/wasm32-wasi/release/wasmedge_quickjs.wasm`

Caused by:
    0: failed to instantiate "target/wasm32-wasi/release/wasmedge_quickjs.wasm"
    1: unknown import: `wasi_snapshot_preview1::sock_setsockopt` has not been defined
```