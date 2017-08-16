# Bitcoin Upgrade at Block 494,784

During the month of November 2017, approximately 90 days after the activation of Segregated Witnesses in the Bitcoin blockchain, a block between 1MB and 2MB in size will be generated by Bitcoin miners in a move to increase network capacity. At this point it is expected that more than 90% of the computational capacity that secures the Bitcoin network will carry on mining on top of this large block.

The upgrade to 2MB blocks has been agreed first during the [Bitcoin Roundtable Consensus in Hong-Kong](https://medium.com/@bitcoinroundtable/bitcoin-roundtable-consensus-266d475a61ff) on February 2016, and then ratified by the [Bitcoin Scaling Agreement in New York](https://medium.com/@DCGco/bitcoin-scaling-agreement-at-consensus-2017-133521fe9a77) on May 2017. These agreements stipulate the activation of Segregated Witness support and an increase of the maximum base block size from 1MB to 2MB.

Segregated Witness support has been locked-in as a soft fork expected to activate around August 23 2017 (block height 481,824). Bitcoin clients that are not currently SegWit-compatible and wish to benefit from the new type of transaction must perform extensive upgrades to various subsystems, including changes to transaction serialization, signature hash computation, block weight calculation, scripting engine, block validation, a new address scheme, and P2P protocol upgrades. Fortunately Segregated Witness compatibility is opt-in, and existing Simplifed Payment Verification (SPV) wallets and full nodes are expected to continue working without changes after SegWit activates.

## Readiness Checklist

The November 2017 upgrade to 2MB blocks is a hard-fork, but necessary changes are trivial to perform. Some SPV clients are expected to work without any change at all. Most clients will need to tweak only two constants to remain compatible with the new larger blocks:

For SegWit-compatible clients:

- Maximum block weight doubles from 4,000,000 to 8,000,000
- Sig-ops per block doubles from 80,000 to 160,000

For non-SegWit-capable clients:

- Maximum base block size doubles from 1,000,000 to 2,000,000
- Sig-ops per block doubles from 20,000 to 40,000

Both types of clients should add new DNS seeds:

- BitPay: seed.mainnet.b-pay.net
- OB1: seed.ob1.io
- Blockchain: seed.blockchain.info
- Bloq: bitcoin.bloqseeds.net

## Testnet5

For testing purposes, a new Testnet5 network that builds on the same Genesis block as the existing Testnet3 network has been created. In order to update a client for compatibility with Testnet5, do these changes to existing Testnet3 settings:

- Port changes from 18333 to 18555.
- Network magic changes from `0x0b110907` to `0x6e657400`
- BIP-34, BIP-66, BIP-65 and single checkpoint all refer to the block at height 10001 with hash `00000000fb7c0a2aeb5f1244e81921b84b7ac770004543144e10c2284f89bfd8`
- DNS seeds are available at `seed.testnet5.b-pay.net` and `bitcoin-testnet.bloqseeds.net`

Block size/weight and sig-ops changes above also apply to Testnet5.

## Compatible Fully-Validating Node Software

- BTC1: https://github.com/btc1/bitcoin
- Bitcoin Unlimited: https://www.bitcoinunlimited.info/
- Bitcoin Classic: https://bitcoinclassic.com/

## Incompatible Fully-Validating Node Software

- Bitcoin Core: https://github.com/bitcoin/bitcoin
- Bitcoin UASF: http://www.uasf.co/