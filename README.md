# zkWASM-specs

zkWASM Specifications

# Start MDBook on your local

## Install Rust

You must install Rust and its toolchain to install mdbook and its dependencies

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## Install mdbook and mdbook-bib

```
cargo install mdbook && cargo install mdbook-bib
```

## Start mdbook server

```
mdbook serve
```

After you run this command, your book will be severed at [http://localhost:3000](http://localhost:3000). Please make sure that port 3000 aren't used.

## License

Licensed under [CC0 1.0 Universal](./LICENSE)

_built with ❤️_
