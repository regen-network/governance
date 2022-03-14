# Decrease Voting Period

This is a parameter change proposal decreasing the voting period for all governance proposals from 14 days to 7 days.

## Background

The Regen Network Development team is planning for smaller and more frequent updates and would like to decrease the voting period in preparation. Decreasing the voting period will also help build a more lively governance process.

The `voting_period` parameter in the `x/gov` module specifies the duration of the voting period for all governance proposals. Since the launch of Regen Mainnet on April 15th, 2021, the `voting_period` has been set to the default value of 14 days (`1209600000000000` nanoseconds). If this proposal passes, the `voting_period` will be updated to 7 days (`604800000000000` nanoseconds).

Other chains in the Cosmos ecosystem have successfully adopted shorter voting periods including Osmosis (with a 3 day voting period) and Juno (with a 5 day voting period). Voting periods less than 7 days were taken into consideration during [the community discussion](https://commonwealth.im/regen/discussion/3762-governance-window-repost-from-discourse-forum) but given the Regen Network community includes land-based/non-tech communities, a 7 day voting period seemed more appropriate.

This proposal is accompanied by [updated proposal guidelines](https://github.com/regen-network/governance) for community members to take into consideration when submitting and voting on proposals. Proposals that do not follow these guidelines might be voted down on principle.
