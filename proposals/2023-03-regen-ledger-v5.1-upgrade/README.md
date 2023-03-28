# Regen Ledger v5.1 Upgrade

This is a software upgrade proposal for the upgrade to Regen Ledger `v5.1`. If passed, this proposal would commit Regen Mainnet to halting the application binary for Regen Ledger `v5.0` at approximately 15:00 UTC on April 5th at block height `10068550` and requiring nodes to restart with the application binary using Regen Ledger `v5.1`.

Validators and node operators can refer to [Upgrade Guide v5.1](https://docs.regen.network/validators/upgrade/v5.1-upgrade.html) for guidelines on performing the upgrade.

Application developers can refer to [Migration Guide v5.1](https://docs.regen.network/ledger/migrations/v5.1-migration.html) for guidelines on migrating their applications.

This upgrade includes a few fixes, improvements, and migrations related to the ecocredit module as well as an update to the latest patch release of Cosmos SDK (v0.46.11).

### Cosmos SDK Update

Regen Ledger v5.0 included an update to the latest version of Cosmos SDK (v0.46.7) using a forked version of Cosmos SDK that adds amino support for the new gov and group modules (a fix that was officially made available in v0.47).

Since the release of Regen Ledger v5.0, several patch releases have been made available. In particular, the v0.46.8 patch release included improvements to the store and therefore a coordinated upgrade is recommended.

At the time of the proposed upgrade, Cosmos SDK will be updated to the latest patch release (v0.46.11) using a forked version with amino support for the gov and group modules.

### Credit Batch Metadata

The schema for metadata referenced within a credit batch has been updated. This is part of a larger effort to provide a consistent standard for all credit batches issued through Regen Registry and to clearly distinguish between data that needs to be anchored on chain and data that is specific to our web application.

Updating to the new schema requires updating the metadata field within each credit batch. Credit batches on Regen Ledger are sealed by default and cannot be updated via state transition functions. This means that an on-chain governance process is required to update the metadata of credits that have already been issued.

At the time of the proposed upgrade, the metadata field within each credit batch will be updated to a new IRI referencing the data stored using the updated schema. The state migration for these changes can be viewed [here](https://github.com/regen-network/regen-ledger/blob/release/v5.1.x/x/ecocredit/migrations/v4/state.go).

### Basket Fixes / NCT Basket

In preparation for the launch of the NCT liquidity pool on Osmosis, the NCT basket was created on Regen Mainnet. At the time of creation, an issue was discovered with setting date criteria using the “years in the past” option. This option sets a requirement on what credits can be put into the basket based on the year of the credit batch start date (i.e. 10 years in the past would mean only credits with a batch start date year of 2013 or later). This option was ignored during basket creation and a fix has been added to prevent this from happening in the future.

In addition, a user error was made at the time of creation and the disable auto-retire option was not set. The default setting when creating a basket is for all credits to be retired when credits are taken from the basket. The intention of the NCT basket is to enable NCT eligible credits to move freely between Polygon (Toucan contracts) and Regen.

At the time of the proposed upgrade, the NCT basket will be updated to include a date criteria with years in the past set to 10 years (according to the NCT standard) and the disable auto-retire option will be set to true (allowing credits to be taken from the basket in a tradable state). The state migration for these changes can be viewed [here](https://github.com/regen-network/regen-ledger/blob/release/v5.1.x/x/ecocredit/migrations/v4/state.go).

In addition, there have been some discussions about updating the NCT standard (specifically the date criteria). As a result, we have included a new governance message that will allow the date criteria of a basket to be updated through a network-wide governance vote.

### Updated Bridge Events

The Toucan-Regen bridge is undergoing a final round of audits and testing. During this process, a few opportunities to simplify event processing were discovered and therefore new event properties have been added to the bridge events within the ecocredit module. The launch of the bridge is not dependent upon these changes.

## Changelog

For a full list of changes since Regen Ledger `v5.0`, please see [CHANGELOG.md](https://github.com/regen-network/regen-ledger/blob/v5.1.0/CHANGELOG.md).
