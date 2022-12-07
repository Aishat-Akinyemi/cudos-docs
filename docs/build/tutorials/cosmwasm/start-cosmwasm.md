---
title: Get started with CosmWasm
id: start-cosmwasm
---

This tutorial gets you started with writing CosmWasm smart contracts. Many thanks to [Callum-A](https://github.com/Callum-A/cosmwasm-zero-to-hero).

## How to use CosmWasm

CosmWasm is a Cosmos SDK module. This means that a binary is enough to start integrating it into your blockchain.

`wasmd` is integrated into the `cudos-noded` binary provided when you follow the instructions to [**Build the binary**](docs/build/build-binary-go).

Using wasmd it is possible to launch a new smart-contract enabled blockchain out of the box, using documented and tested tooling and the same security model as the Cosmos Hub.

A running blockchain is needed to host and interact with the contracts. It can be either localhost, testnet, or a mainnet blockchain.

## 📌 Here's what you need

:::info kit

1. Ideally some **basic Rust knowledge**
2. Understanding of **Git and Github**
3. Comfort using **Terminal and/or CLI**
4. Mac/Ubuntu work machine/Windows - WSL Ubuntu
5. Text editor - **VSCode** or **IntelliJ with Rust Plugin**
6. Ensure you have **Rustup**, **WASM target** and **Cargo Generate** installed. 

If you don't, follow the installation steps on this page: [**Setup Rust**](https://docs.cudos.org/docs/build/setup-rust#install-rust-and-wasm)
:::

## ✏️ 01 Generate boilerplate contract project

Think of a name for your project and enter it as your PROJECT_NAME. 

```shell
cargo generate --git https://github.com/CosmWasm/cw-template.git --name <PROJECT_NAME>
```

### Example - Generate wappy project

```shell
cargo generate --git https://github.com/CosmWasm/cw-template.git --name wappy
🔧   Destination: /Users/adiamond/wappy ...
🔧   project-name: wappy ...
🔧   Generating template ...
? 🤷   Would you like to generate the minimal template?
The full template includes some example logic in case you're new to CosmWasm smart contracts.
The minimal template assumes you already know how to write your own logic, and doesn't get in your way. ›
❯ false
 true
[ 1/24]   Done: .cargo/config 
[ 2/24]   Done: .cargo 
[ 3/24]   Skipped: .circleci/config.yml 
[ 4/24]   Done: .circleci 
[ 5/24]   Done: .editorconfig 
[ 6/24]   Done: .github/workflows/Basic.yml 
[ 7/24]   Done: .github/workflows/Release.yml  
[ 8/24]   Done: .github/workflows 
[ 9/24]   Done: .github 
[10/24]   Done: .gitignore
[11/24]   Done: Cargo.lock 
[12/24]   Done: Cargo.toml
[13/24]   Done: LICENSE 
[14/24]   Done: NOTICE 
[15/24]   Done: README.md 
[16/24]   Done: src/bin/schema.rs 
[17/24]   Done: src/bin 
[18/24]   Done: src/contract.rs
[19/24]   Done: src/error.rs
[20/24]   Done: src/helpers.rs
[21/24]   Done: src/lib.rs 
[22/24]   Done: src/msg.rs
[23/24]   Done: src/state.rs
[24/24]   Done: src    🔧   Moving generated files into: `/Users/user/wappy`...
💡   Initializing a fresh Git repository
✨   Done! New project created /Users/user/wappy
```

## 📂 02 Explore inside the project?

```shell
cw-starter/ # Root
├── .cargo/
│   └── config # Configuration for cargo commands such as cargo wasm, cargo schema, etc.
├── .circleci/
│   └── config.yml # Circle CI workflows and integration
├── .github/workflows/
│   └── Basic.yml # GitHub actions integration
├── examples/
│   └── schema.rs # Rust file to generate JSON schema via cargo schema. Outputs to schema/
├── schema/ # Output folder for JSON schema
├── src/ # Where our smart contract rust files are located
│   ├── contract.rs # Main contract logic, instantiate, execute, query
│   ├── error.rs # Where we define our contract errors
│   ├── lib.rs # Where we define our modules
│   ├── msg.rs # Where we define our message types
│   └── state.rs # Where we define any state variables
└── target/ # Where unoptimised WASM files are outputted
├── cargo.toml # Where dependencies are specified
```

## 03 What we're going to build

We're going to build and store polls on chain. 
Here is how our app will work: 

1. Any user can create a poll.
2. Any user can vote on a poll.
3. Polls can have different options.

Let's imagine Dorothy Parker has created a poll. Here's an example of how it looks:

:::note Example Poll

What is your favourite Cosmos ecosystem project?
a. Cudos
b. Osmosis
c. Cosmos Hub
:::

1. Dorothy can vote in her own poll. She votes for Cudos. 
2. William Blake decides to vote for Cosmos Hub. 
3. Dorothy decides to end the poll after 30 minutes.
4. Rabindranath Tagore attempts to vote but is too late!
5. Everyone can see the results of the poll.


## 02 Generate a WASM file

1. Change to the root directory of the project

```shell
cd project-name
```

2. Run command

Build an unoptimised WASM file. 

```shell
cargo wasm
```

This file is located at **target/wasm32-unknown-unknown/release/cw_starter.wasm**

## 03 Optimise the file







