# IBC Patch Upgrade

The recent upgrade to Regen Ledger v2 was a great success. However there's a bug in the integration, which created an issue for IBC transfers. IBC transfers are not going through currently due to a missing migration for the IBC module. Regen Ledger v2.1.0 fixes that and this proposal is to conduct an emergency upgrade to avoid any further potential issues with IBC client expiry. If IBC clients expire, the funds would get stuck in the expired channel, so we need to upgrade the network to fix this before IBC clients expire.

This proposal expects every validator to update their regen software to v2.1.0 before the block height 3126912 and then to vote on this proposal. A yes vote on this proposal conveys that the validator has updated their binaries to v2.1.0.

Estimated update time is Friday, 26th Nov, 1700UTC.

## Upgrade Instructions

Please make sure to switch to the new software version on all of your nodes before block height `3126912` is committed on chain. If 67% of voting power does not upgrade to this version by this block height then the network will halt due to consensus failure.

Build and install the `regen` binary using regen-ledger version `v2.1.0`:

```
git clone https://github.com/regen-network/regen-ledger
cd regen-ledger
git fetch --all
git checkout v2.1.0
make install
make build
```

Check the version to make sure the install was successful:

```
regen version
```

You should see `v2.1.0` printed to the console.

If you're using cosmovisor copy the new binary to the `v2.0-upgrade` directory.
    
```
cp $HOME/regen-ledger/build/regen $HOME/.regen/cosmovisor/upgrades/v2.0-upgrade/bin
```

After moving the binary restart your cosmovisor process:

```
sudo systemctl restart cosmovisor.service
```

If you're not using cosmovisor, simply restart your systemd process with the new binary:

```
sudo systemctl restart regen.service
```