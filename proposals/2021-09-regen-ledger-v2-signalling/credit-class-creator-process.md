# Process For Becoming a Credit Class Creator

Version: 1

## Background

With the launch of Regen Ledger v2.0, we are excited to bring the first version of the ecocredit module to Regen Mainnet. This module is intended to be used for the issuance, tracking, trading, and retiring of ecosystem service credits managed on Regen Ledger.

Over the next several months, the Regen Network Development (RND) team plans to further refine the requirements and specifications for the ecocredit module, therefore, the API for issuing and managing on-chain ecological assets may change in upcoming versions of Regen Ledger. For this reason, we’re proposing to launch the ecocredit module as a permissioned module, in which the creation of new classes of ecosystem service credits, herein called “credit classes”, will be restricted to a permissioned set of addresses defined in an allowlist that is governed by the Regen Network token holder community. The list of approved credit class creators would be an on-chain parameter that can only be updated through the Regen Ledger governance proposal process.

This document intends to outline a basic rubric for evaluating organizations and individuals wanting to be on the allowlist for credit class creators. These guidelines are intended to help the Regen Network token holder community align on a process for evaluating candidacy, as well as to help potential applicants understand how to demonstrate their qualifications for being a credit class creator in this initial stage of building out a platform for ecosystem service credits.

Regen Registry plans to submit a proposal to be one of the first candidates for this process, enabling RND to create credit classes for methodologies created by our team as well as ones submitted through the Regen Registry program. If you’re an active methodology designer and you aren’t ready or you don’t want to undertake the process of becoming a credit class creator on Regen Ledger, we welcome you to engage with the [Regen Registry program](https://registry.regen.network/create-methodology). 

## Credit Class Primer

*This section provides a short overview of what a credit class is and how it will be represented on-chain as of Regen Ledger 2.0. For the most up-to-date information about the ecocredit module and the credit class, see the [ecocredit module specification](https://docs.regen.network/modules/ecocredit/).*

Within the context of Regen Ledger, a credit class is a data object stored on-chain that defines the ecosystem service credit. New credit classes are created via an on-chain transaction (by an approved credit class creator initially), and credits from a credit class are issued in discrete batches over time. In the Baikal Upgrade (Regen Ledger v2.0), creation of new credit classes will be limited to a finite set of users defined in the `allowed_class_creators` on-chain parameter. In the future, it is expected that credit class creation will be permissionless.

Every credit class is associated with a single credit type, which is the primary indicator used to measure the change or impact resulting from an ecosystem service. The list of credit types, like the list of credit class creators, is an on-chain parameter. In order to create a credit class with a credit type not already listed on the approved list of credit types, the credit type will also need to be added through the Regen Ledger governance proposal process. The list of credit types will be initiated with a single, default “carbon” credit type with the following properties:

Name: "carbon"
Abbreviation: "C"
Unit: "metric ton CO2 equivalent"
Precision: 6

A credit class includes a metadata field intended to be used as a pointer to a linked document which defines a list of methodologies which can be used to measure and monitor changes in ecological state. The linked document would define the structure, procedures, and requirements of the methodologies as well as the project eligibility requirements required for that type of project. The metadata is represented as a finite length byte array. The metadata will likely be a URI or CID hash or a JSON object that includes multiple URIs or CID hashes.

### Credit Class Creator

A credit class creator is an address with the authority to create credit classes. The list of approved credit class creators is stored as an on-chain parameter that can only be updated through the governance process. Credit classes can be created by executing a transaction on-chain with the required credit type, metadata, and list of approved issuers. Upon creation of a credit class, the credit class creator is set as the admin for the given credit class.

### Credit Class Administrator

The credit class administrator (`CreditClassAdmin` as represented in code) is defined within a credit class as the address with the authority to manage and update the credit class. The credit class admin will have the ability to transfer the admin role to another address, manage the list of credit class issuers, and change credit class metadata.

### Credit Issuers

The credit issuers are defined within a credit class as a list of addresses with the authority to issue credit batches of the corresponding credit class. The list of credit issuers are defined at the time the credit class is created. The credit class admin will be able to manage the list of credit issuers for the credit class they administer.

## Who should apply to become a credit class creator?

An individual or organization wanting to become an approved credit class creator should have an ability to design and/or evaluate robust ecosystem service credits and methodologies and a willingness to manage on-chain assets. A credit class creator might be a methodology designer themselves or they might be working with one or multiple methodology designers.

Applicants should check if a credit class already exists for their desired methodology and consider becoming an issuer for that credit class if appropriate.

## Credit Class Creator Guidelines

The following guidelines are intended to help the Regen Network token holder community align on a process for evaluating candidacy, as well as to help potential applicants understand how they might demonstrate their qualifications for being a credit class creator.

### Be actively engaged in the design & development of ecosystem service credits

An applicant should provide a document that outlines a proposed methodology (or multiple documents that outline multiple methodologies) and/or supporting documentation and resources on their design and evaluation process if they plan to partner with methodology developers.

As an example, when the Regen Registry team submits their governance proposal for becoming a credit class creator, they may provide links to the CarbonPlus Grasslands [documentation](https://regen-registry.s3.amazonaws.com/Methodology+for+GHG+and+Co-Benefits+in+Grazing+Systems.pdf), as well as links to the more general registry program guides ([creating a methodology](https://regen-registry.s3.amazonaws.com/process-for-creating-a-methodology.pdf), [methodology framework](https://docs.google.com/document/u/2/d/1ccQRkhc5fDv1qTtlh7EEJ6eZsJ4IqtbU0Cwd_lwiI5A/edit)) to demonstrate how they are actively engaging in the process of developing ecosystem service credits.

### Demonstrate desire and capacity to work with the Regen Ledger maintainers to migrate credit class data when breaking changes are introduced to the ecocredit module

As mentioned above, we expect that the data model for the ecocredit module may change in later releases of Regen Ledger. In order to ensure any credit classes created with Regen Ledger v2.0 are properly migrated, credit class creators will need to keep up with potential data schema changes, working with the software and community to ensure credit class data is migrated appropriately. Demonstrating desire and capacity to work with software and community on the data migration could be accomplished by socializing commitment and understanding within the proposal and by being an active member of the community as well as demonstrating technical expertise.

### Socialize candidacy as a credit class creator

All governance proposals for adding an address to the approved list of credit class creators should start with a forum post outlining the proposal that links to relevant qualifications and documentation, and that socializes commitment and understanding to work with the Regen community. The forum post should receive general support from the community before being submitted as an on-chain governance proposal.
