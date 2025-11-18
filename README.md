
# DTU Student Verification Plugin for TLSNotary


This repository contains my implementation of the TLSN boilerplate, developing a plugin for the TLSNotary browser extension to verify a DTU student account. This project is part of my Bachelor's Thesis on TLSN, conducted with Jázmin Seregi and supervised by Carsten Baum and Chiara-Marie Zok. 

This repository is based on the TLSN Boilerplate by [TLSNotary](https://github.com/tlsnotary/tlsn-plugin-boilerplate.git).

## Features

- Verifies DTU student accounts via TLSNotary
- Built with TypeScript and Extism
- Compatible with TLSNotary browser extension
- Uses WebAssembly (WASM) for plugin execution

## Prerequisites

- Node.js and npm installed
- Rust installed (for building the proxy server, but here other options are possible)
- Access to the TLSNotary web extension

## Installation of Extism-js
TLSNotary's plugin system uses [Extism](https://github.com/extism), which enables plugins in different programming languages. For more documentation, check [Extism's documentation](https://github.com/extism/js-pdk).

1. **Download and Install Extism-js**: Begin by setting up `extism-js`, which enables you to compile and manage your plugins. Run these commands to download and install it:

    ```sh
    curl -O https://raw.githubusercontent.com/extism/js-pdk/main/install.sh
    bash install.sh
    ```

    This script installs the Extism JavaScript Plugin Development Kit from its GitHub repository, preparing your environment for plugin compilation.

## Building the DTU Account Plugin

To build the plugin, redirect your terminal to DTU_account and run:

```sh
npm i
npm run build
```

This will output the wasm binary in `dist/index.wasm`.

### Running the DTU Plugin Example

1. Build the `DTU_account` plugin as explained above.
2. Build and install the `tlsn-extension` as documented in the [main README.md](https://github.com/tlsnotary/tlsn-extension/blob/main/README.md).
3. [Run a local Notary server](https://github.com/tlsnotary/tlsn/blob/main/crates/notary/server/README.md). I personally used their : https://notary.pse.dev/v0.1.0-alpha.12
4. [Run a local Proxy Server to allow TPC,](https://tlsnotary.org/docs/notary_server). I personally used:
    ```sh
        cargo install wstcp
        wstcp --bind-addr 127.0.0.1:55688 learn.inside.dtu.dk:443
    ```
    I have shared an example of how to put this in the settings as a screenshot. 
5. Run the plugin

![Setting for Proxy and Notary Server](assets/screenshot.png)

<p align="center">
  <img src="assets/screenshot.png" width="400">
</p>

## Credits
    Based on the TLSN Boilerplate by TLSNotary
