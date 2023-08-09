# Parachain Guide Resources

> _This is meant to be followed with the [Parachain Development Guide by W3F](https://education.web3.foundation/docs/introparachain)_.
> Be sure to set the `substrate-parachain-template` to version 
This repository contains the **compiled** runtimes, JSON, and SCALE encoded chain specifications for quickly running a local, native relay and parachain setup.

This is primarily for learning purposes and to learn at a more granular level how to provision networks from scratch.  For a more ready-made solution to provision and spawn networks which includes a CLI, please use [Zombienet](https://github.com/paritytech/zombienet).

## Parachain

The parachain here is based off of the Cumulus template: [substrate-parachain-template]().  It is able to be modified and compiled if needed:

```bash
# Make sure you're in the correct branch/version (1.0.0)
cd substrate-parachain-template/
git checkout polkadot-v1.0.0
git switch -c parachain-v1.0.0

# Build the chain
cargo build --release

# Build initial chain spec 
./target/release/parachain-template-node build-spec > ../parachain/parachain_chain_spec.json  

# Build the raw chain spec
./target/release/parachain-template-node build-spec --chain ../parachain/parachain_chain_spec.json --disable-default-bootnode --raw > ../parachain/parachain_chain_spec_raw.json

# Compile the Wasm bundle
./target/release/parachain-template-node export-genesis-wasm --chain ../parachain/parachain_chain_spec_raw.json parachain-wasm

# Compile the genesis bundle
./target/release/parachain-template-node export-genesis-state --chain ../parachain/parachain_chain_spec.json ../parachain/parachain-genesis-state 
```

### Chain Specification

The chain specification is based off of the default template.  If you wish to modify this, consider recompiling the node and regenerating as per above.

### Runtime & Genesis

Both are based off of the default template with no added modifications.

## Relay Chain

The relay chain configuration is a `rococo_local` testnet.  The relay chain does not need much - but you msut have the `polkadot` binary installed and in your path in order to successfully run the commands.


