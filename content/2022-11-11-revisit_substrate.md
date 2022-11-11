+++
title = "Revisiting Substrate"
date = 2022-11-11

[taxonomies] 
tags = ["blockchain", "rust", "substrate"]
+++

After 2 years, it is time to sit down and get substrate compiled again. The framework has changed a lot with literally thousands of commits around the clock. The architecture fundamentally changed, and many essential components are either further moved into higher abstract layers of libraries, or removed.

Here are the steps to get substrate compiled:

1. Make sure that all the dependencies are installed. (In this article, Fedora 36 is the chosen platform.)


- Install Rust & nightly

```
# download rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# switch to the nightly version
rustup default nightly

# update
rustup update
```

- Install WASM Compiler

`rustup target add wasm32-unknown-unknown`

- Install Other Dependencies

protobuf-compiler

`sudo dnf install protobuf-compiler`

g++

`sudo dnf install g++`

clang

`sudo dnf install clang`

2. Get the source code

Clone the source from github

`git clone https://github.com/paritytech/substrate.git && cd substrate`

Compile

`cargo +nightly build --release`

Wait for the compile, (depends on how fast the machine is)

And at Last,

`cargo run -- --dev`


If everything is done right, the following strings will appear on the terminal.

```
2022-11-11 13:08:07 Substrate Node
2022-11-11 13:08:07 ✌️  version 3.0.0-dev-a1dee7ecd2a
2022-11-11 13:08:07 ❤️  by Parity Technologies <admin@parity.io>, 2017-2022
2022-11-11 13:08:07 📋 Chain specification: Development
2022-11-11 13:08:07 🏷  Node name: huge-reason-1707
2022-11-11 13:08:07 👤 Role: AUTHORITY
2022-11-11 13:08:07 💾 Database: RocksDb at /tmp/substratelipvJS/chains/dev/db/full
2022-11-11 13:08:07 ⛓  Native runtime: node-268 (substrate-node-0.tx2.au10)
```

And yes, compiling the stock node for local development is done here.

- What's next ?

If someone wants only do some smart contract development, then it should be OK just using the local development node.

Or, if further modification to the blockchain itself is needed, for example, changing the consensus algorism, the sourcecode itself needs to be modified. And this will be written about in future articles.
