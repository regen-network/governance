# Regen Ledger v4.1 Upgrade

This is a software upgrade proposal for the upgrade to Regen Ledger v4.1.1. If passed, this proposal would commit Regen Mainnet to halting the application binary for Regen Ledger v4.0 at block height 7479500 (approximately 16:00 UTC on Friday, October 7th) and starting the application binary for Regen Ledger v4.1.1.

## Summary

Recently the core developers of Regen Ledger were made aware of two bugs in Regen Ledger v4.0 that we deemed important to fix before the previously anticipated Regen Ledger v5.0. Both of these bugs required consensus-breaking changes to Regen Ledger. The developers have prepared a single upgrade (Regen Ledger v4.1.1) which contains both fixes, to ease the burdon on validators and not have to do two separate consecutive upgrades.

## Validator Updates not propagating to Tendermint

As of Regen Ledger v4.0, Tendermint has not been receiving validator updates from the application state. This was initially reported by a member of our validator community. What resulted is that the actual block-signing validator set (managed by Tendermint) essentially froze as of the upgrade to Regen Ledger v4.0.

Validators who had been jailed or otherwise unbonded were not actually removed from the validator set managed by Tendermint. Any new validators who were supposed to be promoted to the active validator set were not actually admitted into the block-producing validator set managed by Tendermint.

Upon being notified of the issue, the dev team analyzed the situation and determined that there was no risk of consensus failure and that it was safe to proceed with a software upgrade proposal (1-week voting time), as opposed to requiring an emergency rolling-upgrade.

A fix for this issue has been implemented in Regen v4.1. It will, at the scheduled upgrade height, update Tendermint's validator set to the correct active set (as managed by the application). In other words, all validators who should have been jailed since the upgrade to v4.0 will be immediately removed from Tendermint's validator set, and any new validators waiting to be admitted into the active set will be immediately added to tendermint's block-producing validator set.

## Amino Signing of Ecocredit Transactions

Recently a bug was identified in how regen ledger serializes ecocredit transactions for Amino signing. When signing ecocredit transactions with a hardware wallet regen ledger mis-implements amino serialization, deviating from the behavior expected by javascript clients (namely Keplr wallet and CosmJS). As a result, hardware wallets could not be used for signing transactions initiated from a browser based application. (note: hardware wallet signing using the regen CLI was unaffected, and worked as expected).

A fix for this issue has been implemented in v4.1.1. It fixes amino serialization such that Keplr and CosmJS can now be used to generate, sign, and broadcast transactions involving ecocredit functionality on Regen Network.


## Changelog

For a full list of changes since Regen Ledger v4.0, please see [CHANGELOG.md](https://github.com/regen-network/regen-ledger/blob/v4.1.1/CHANGELOG.md).
