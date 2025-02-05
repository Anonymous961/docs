---
sidebar_label: Taro testnet
description: The first testnet built with OP Stack and Celestia.
---

# Taro testnet

![Taro testnet](../../static/img/Celestia_Taro_Testnet.png)

[Taro Testnet](https://tarotestnet.com) is a fresh offering from
[Caldera](https://caldera.xyz) with support from Celestia Labs,
built with OP Stack and Celestia, and is dedicated to providing developers with
an EVM-compatible execution layer to deploy their EVM applications on.

## Built with the OP Stack and Celestia

The Taro Testnet is a testnet rollup, a modified version of
`optimism-bedrock` that uses Celestia as a data availability (DA)
layer. This integration can be found in this
[repository](https://github.com/celestiaorg/optimism). The testnet
is hosted by [Caldera](https://caldera.xyz), who makes it easy to launch
rollups with no code required.

In this setup, data handling is accomplished in two ways. Firstly, data is
written to the DA layer, in this case, Celestia
(on the [Arabica devnet](../../nodes/arabica-devnet)). Then, the data
commitment is written to the `op-batcher`. When reading, the `op-node`
retrieves the data back from the DA layer by first reading the data commitment
from the `op-batcher`, then reading the data from the DA layer using the data
commitment. Hence, while previously `op-node` was reading from `calldata` on
Ethereum, it now reads data from Celestia.

The tools involved in the data handling process include `op-batcher`,
which batches up rollup blocks and posts them to Ethereum, `op-geth`
that handles execution, and `op-proposer` responsible for state commitment
submission.

By using Celestia as a DA layer, existing L2s can switch from posting their
data as `calldata` on Ethereum to posting to Celestia. The commitment to the
block is posted on Celestia, which is purpose-built for data availability.
This is more scalable than the traditional method of posting this data as
`calldata` on monolithic chains.

## Building on Taro

Taro Testnet provides a robust environment for developers to test their
Ethereum Virtual Machine (EVM) applications. It offers an EVM-compatible
execution layer, making it an ideal platform for developers looking to
build and test applications in a setting that closely mirrors an OP Stack
rollup on Celestia.

Learn more at [tarotestnet.com](https://tarotestnet.com).

### RPC URLs

Remote Procedure Call (RPC) URLs are endpoints that allow developers to
interact with the blockchain. They are essential for sending transactions,
querying blockchain data, and performing other interactions with the
blockchain.

For the Taro Testnet, you can connect to the following RPC URLs:

#### HTTPS

* `https://taro-testnet.calderachain.xyz/http`

#### WSS

* `wss://taro-testnet.calderachain.xyz/ws`

This URL serves as the entry point to the Taro Testnet. You can use it
in your applications to connect to the testnet and interact with the smart
contracts you deploy there.

Remember, Taro Testnet is a testing environment!

### Faucet

To visit the Taro testnet faucet, go to
[`https://tarotestnet.com`](https://tarotestnet.com).

### Explorer

To visit the explorer, go to
[`https://explorer.tarotestnet.com/`](https://explorer.tarotestnet.com/).

## Next steps

Now that you have a better understanding of the Taro Testnet and its
integration of OP Stack and Celestia, you can start exploring its
capabilities:

* [Deploy a smart contract on Taro testnet](../deploy-on-taro)
* [Deploy a GM Portal dapp on Taro testnet](../gm-portal-taro)
<!-- * [Deploy a dapp with scaffold-eth](https://github.com/jcstein/scaffold-eth) -->
* [Deploy a smart contract with Thirdweb](https://thirdweb.com/taro-testnet)
