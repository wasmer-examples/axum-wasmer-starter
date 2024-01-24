This is an [Axum](https://github.com/tokio-rs/axum) Web Server starter template that compiles to [WASIX](https://wasix.org).

> Checkout the full tutorial [here](http://wasix.org/docs/language-guide/rust/tutorials/wasix-axum)


## Getting started

First, build the project using [`cargo-wasix`](https://crates.io/crates/cargo-wasix):

```bash
$ cargo wasix build
```

Then, you can run the server easily using Wasmer:

```bash
$ wasmer run . --net --env PORT=8080
Listening on http://127.0.0.1:8080
```

> [!NOTE]
> You will need to have Wasmer installed (check out [the docs to install the Wasmer CLI](https://docs.wasmer.io/install)!). 
> The `--net` flag is required to enable networking support in Wasmer. The `PORT` environment variable is required to run the server locally.

## Deploy on Wasmer Edge

The easiest way to deploy your WCGI Rust app is to use the [Wasmer Edge](https://wasmer.io/products/edge).

Live example: https://wasix-axum-example.wasmer.app

```bash
wasmer deploy
```

> [!NOTE]
> You will need to change the namespace in `wasmer.toml` to your own namespace and app name in `app.yaml` to your own app name.

