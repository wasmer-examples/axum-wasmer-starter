# Axum Web Server + Wasmer

This example shows how to run a minimal **Axum** HTTP server compiled to **WASIX** on **Wasmer Edge**.

## Demo

`https://<your-subdomain>.wasmer.app/` (deploy to get a live endpoint)

## How it Works

`src/main.rs` creates a single-route Axum application:

* `Router::new().route("/", get(handler))` registers one handler that returns `"Hello, Axum ❤️ WASIX!"`.
* The server reads the `PORT` environment variable (default `80`) so it matches Wasmer’s assigned port.
* `axum::Server::bind(&addr).serve(...)` launches the async server on top of Tokio.

Because the target is WASIX, the project builds to a `.wasm` binary that Has its own WASI-compatible networking stack.

## Running Locally

```bash
cargo build --target wasm32-wasmer-wasi
wasmer run target/wasm32-wasmer-wasi/debug/skip-rust-axum.wasm --env PORT=3000
```

Open `http://127.0.0.1:3000/` to see the greeting. (You can also `cargo run` for a native build during development.)

## Deploying to Wasmer (Overview)

1. Build the WASIX binary: `cargo build --target wasm32-wasmer-wasi --release`.
2. Reference the output module in `wasmer.toml` and expose the `_start` entrypoint.
3. Deploy to Wasmer Edge and visit `https://<your-subdomain>.wasmer.app/`.
