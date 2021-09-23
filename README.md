# Architecture

This project specifies the network and dataflow architecture of Accumulate.

## General

For a more complete picture of the general system architecture, refer to the
[litepaper](https://accumulatenetwork.io/litepaper/).

Every network transaction is associated with an Accumulate Digital Identifier
(ADI). The Accumulate network consists of multiple Block Validator Chains
(BVCs) and a Directory Chain (DC). Each transaction is routed to a particular
BVC based on the SHA–256 has of the authoring ADI. Periodically, each BVC
pins its current state to the DC. If the recipient ADI is routed to a different
BVC, the authoring BVC creates a synthetic transaction and submits it to the
recipient BVC. The recipient BVC validates the synthetic transaction by
verifying that the transaction exists in the authoring BVC and is pinned by the
DC.
