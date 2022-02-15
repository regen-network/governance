# Regen Ledger v2.2 Upgrade

This is a software upgrade proposal for the upgrade to Regen Ledger v2.2. If passed, this proposal would commit Regen Mainnet to halting the application binary for Regen Ledger v2.1 at approximately 16:00 UTC on March 5th and starting the application binary for Regen Ledger v2.2.

Validators and node operators can refer to the [v2.2 migration documentation](https://docs.regen.network/migrations/v2.2-upgrade) for guidelines on performing the upgrade.

## Regen Ledger v2.2

Regen Ledger v2.2 updates the ecocredit module to include basket functionality, enabling the aggregation of heterogeneous ecosystem service credits into baskets. Credits from different classes and batches that meet a defined criteria can be deposited within a basket in exchange for basket tokens. The basket tokens are fully fungible with other tokens from the same basket and each basket token can be redeemed for an ecocredit from the given basket.

With the recent solidification of the NCT standard, we are proposing an accelerated timeline to make such an asset available in the Cosmos ecosystem. v2.2 includes a scoped-down, minimum-viable basket implementation with the intention to bring IBC compliant carbon credits to the interchain. For more information about the intended basket functionality, see the [basket specification](https://github.com/regen-network/regen-ledger/blob/master/rfcs/002-baskets-specification.md).

Regen Registry will be creating a single credit class for Verra VCU credits and will be managing a bridging process to bring these assets from Verra registry to Regen Network. While the creation of this credit class and the issuing of all of these credits is something that can happen with the current version live on mainnet (v2.1), the basket module is required in order to move these assets to other blockchains within the Cosmos ecosystem via IBC. 