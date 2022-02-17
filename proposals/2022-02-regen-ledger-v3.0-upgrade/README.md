# Regen Ledger v3.0 Upgrade

This is a software upgrade proposal for the upgrade to Regen Ledger v3.0. If passed, this proposal would commit Regen Mainnet to halting the application binary for Regen Ledger v2.1 at approximately 16:00 UTC on March 5th and starting the application binary for Regen Ledger v3.0.

Validators and node operators can refer to the [v3.0 migration documentation](TBD) for guidelines on performing the upgrade.

## Background

With the [cosmos carbonZERO earth program](https://earthstate.ixo.world/zero/), and other Cosmos ecosystem demand for carbon credits on the rise, the RND Inc team feels it is important for ecocredits to have the ability to be exported to the interchain world.

The current demand for carbon offsets from Regen Ledger is estimated to be above 80,000 tons per year simply to offset the "Scope 1" emissions (validator infrastructure emissions) of the cosmos ecosystem at this moment, and this does not consider the potential for carbon credits to find other markets and uses beyond simply offsetting the blockchain infrastructure securing the internet of blockchains. We believe this will anchor Regen Network's utility and relationship with the larger internet of blockchains and is a significant next step for our community.

In order to meet this demand the RND Inc team is proposing an upgrade to Regen Ledger, the details of which are shared below.

## Regen Ledger v3.0

Regen Ledger v3.0 updates the ecocredit module to include basket functionality, enabling the aggregation of heterogeneous ecosystem service credits into baskets. Credits from different credit classes and batches that meet a defined criteria can be deposited within a basket in exchange for basket tokens. The basket tokens are fully fungible with other tokens from the same basket, and are tracked in the standard Bank module, which means these assets will be made visible in wallets like Keplr, and also able to be transfered via IBC to other chains in the Cosmos ecosystem. Each basket token can later be redeemed for an underlying ecocredit from the given basket, and the ecocredits received may be retired by the account receiving them (for offseting emissions).

For more information about the full specification for basket functionality, see the [basket specification](https://github.com/regen-network/regen-ledger/blob/master/rfcs/002-baskets-specification.md).

With the recent solidification of the [NCT standard](https://docs.toucan.earth/protocol/pool/pool-parties/nct-pool-party-report), we are proposing an accelerated timeline for the baskets module to bring NCT's into the Cosmos ecosystem.

Regen Ledger v3.0 includes a scoped-down, minimum-viable basket implementation with the intention to bring IBC compliant carbon credits to the interchain. 

The MVP version of baskets proposed in Regen Ledger v3.0 differs from the full specification in the RFC above in that:

- `BasketCritera` is restricted to only allow for:
  - A list of credit classes
  - A recency filter reprsented either as a fixed minimum batch start date, or a rolling recency window (e.g. batch start date must be within the last 6 months)
- Retreiving ecocredits from a basket can only be done via `Take`, not `Pick`. All calls of `Take` will always retreive the oldest ecocredits first (by batch start date), ensuring the basket flushes out old credits over time.

## Bringing the NCT to the Interchain Ecosystem

In conjunction with this proposed upgrade, Regen Registry will be creating a single credit class for Verra VCU credits and will initially manage a manual bridging process to bring assets from Verra registry to Regen Network as ecocredits. This credit class is intended to match with the inclusion criteria proposed for the [NCT Standard](https://docs.toucan.earth/protocol/pool/pool-parties/nct-pool-party-report). While the creation of this credit class and the issuing of these credits is something that can happen with the current version live on mainnet (v2.1), the basket module proposed for Regen Ledger v3.0 will enable these ecocredits to be convernted into a fungible, IBC-compatible token, bringing this new standard for nature based carbon credits into the interchain ecosystem.
