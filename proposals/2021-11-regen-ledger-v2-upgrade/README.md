# Regen Ledger v2.0 Upgrade

This is a software upgrade proposal for the upgrade to Regen Ledger v2.0. If passed, this proposal would commit Regen Mainnet to halting the application binary for Regen Ledger v1.0 at approximately 16:00 UTC on Nov 16th and starting the application binary for Regen Ledger v2.0.

Validators and node operators can refer to the [v2.0 migration documentation](https://docs.regen.network/migrations/v2.0-upgrade) for guidelines on performing the upgrade.

## Regen Ledger v2.0

Regen Ledger v2.0 includes an upgrade to Cosmos SDK v0.44 and the addition of three new modules: the authz module, the feegrant module, and the ecocredit module.

### Cosmos SDK

Regen Mainnet is currently running Regen Ledger v1.0 with Cosmos SDK v0.42. The upgrade to Regen Ledger v2.0 includes an update to Cosmos SDK v0.44. For more information about Cosmos SDK v0.43 and Cosmos SDK v0.44, see the release notes:

- [Cosmos SDK v0.43.0 Release Notes](https://github.com/cosmos/cosmos-sdk/blob/release/v0.43.x/RELEASE_NOTES.md)
- [Cosmos SDK v0.44.0 Release Notes](https://github.com/cosmos/cosmos-sdk/blob/release/v0.44.x/RELEASE_NOTES.md)

### Authz Module

The authz module enables a granter to grant an authorization to a grantee that allows the grantee to execute a message on behalf of the granter. For more information about the authz module, see the [Authz Module Specification](https://docs.cosmos.network/master/modules/authz/).

### Feegrant Module

The feegrant module enables the ability for a granter to grant an allowance to a grantee where the allowance is used to cover fees for sending transactions. For more information about the feegrant module, see the [Feegrant Module Specification](https://docs.cosmos.network/master/modules/feegrant/).

### Permanent Locked Accounts

Regen Ledger v2.0 supports the on-chain creation of permanent locked accounts through the `MsgCreatePermanetLockedAccount` message. These special types of accounts are intended to be used by Regen Foundation for seeding Community Staking DAOs, wherein the initial REGEN funds distributed to these accounts must be permanently locked and only usable for governance and staking. For more information see [regen-ledger#188](https://github.com/regen-network/regen-ledger/issues/188)

### Ecocredit Module

The ecocredit module enables the ability to manage classes of ecosystem service credits and to mint credits through a batch issuance process. For more information about the ecocredit module, see the [Ecocredit Module Specification](https://docs.regen.network/modules/ecocredit/).
