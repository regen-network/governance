# Regen Ledger v2.0 Upgrade

This is a software upgrade proposal for the upgrade to Regen Ledger v2.0. If passed, this proposal would commit Regen Mainnet to halting the application binary for Regen Ledger v1.0 at 16:00 UTC on Nov 15th and starting the application binary for Regen Ledger v2.0.

## Regen Ledger v2.0

Regen Ledger v2.0 includes an upgrade to Cosmos SDK v0.44 and the addition of three new modules: the authz module, the feegrant module, and the ecocredit module.

### Cosmos SDK

Regen Mainnet is currently running Regen Ledger v1.0 with Cosmos SDK v0.42. The upgrade to Regen Ledger v2.0 includes an update to Cosmos SDK v0.44. For more information about Cosmos SDK v0.43 and Cosmos SDK v0.44, see the release notes:

- [Cosmos SDK v0.43.0 Release Notes](https://github.com/cosmos/cosmos-sdk/blob/release/v0.43.x/RELEASE_NOTES.md)
- [Cosmos SDK v0.44.0 Release Notes](https://github.com/cosmos/cosmos-sdk/blob/release/v0.44.x/RELEASE_NOTES.md)

### Authz Module

The authz module enables a granter to grant an authorization to a grantee that allows the grantee to execute a message on behalf of the granter. For more information about the authz module, see the specification:

- [Authz Module Specification](https://docs.cosmos.network/master/modules/authz/)

### Feegrant Module

The feegrant module enables the ability for a granter to grant an allowance to a grantee where the allowance is used to cover fees for sending transactions. For more information about the feegrant module, see the specification:

- [Feegrant Module Specification](https://docs.cosmos.network/master/modules/feegrant/)

### Permanent Locked Accounts

Regen Ledger v2.0 supports the on-chain creation of permanent locked accounts through the `MsgCreatePermanetLockedAccount` Msg and via CLI. These special types of accounts are intended to be used by Regen Foundation for seeding Community Staking DAOs, wherein the initial REGEN funds distributed to these accounts must be permanently locked and only usable for governance and staking.

For more information see [regen-ledger#188](https://github.com/regen-network/regen-ledger/issues/188)

### Ecocredit Module

The ecocredit module enables the ability to manage classes of ecosystem service credits and to mint credits through a batch issuance process. For more information about the ecocredit module, see the specification:

- [Ecocredit Module Specification](https://docs.regen.network/modules/ecocredit/)

## Permissioned Credit Class Creators

The ecocredit module supports the option of restricting credit class creation to a permissionned set of addresses. This list of allowed credit class creators is an on-chain parameter that can only be updated through the governance process. This option will be enabled at the time of upgrade, meaning the ecocredit module will start with a permissioned approach to credit class creation.

With this approach, the Regen Network community (REGEN token holders) will ultimately decide which addresses are included on the allowlist. The list of permissionned credit class creators on Regen Mainnet will initially be empty. The RND team plans to submit a subsequent proposal adding an RND owned address to the allowlist, following the same process that other individuals and organization are being asked to follow. For more information about the criteria and process for becoming a credit class creator, see the following document:

- [Credit Class Creator Process](./credit-class-creator-process.md)
