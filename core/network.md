# Core Network Architecture

Each BVC exists as an independent Tendermint network, and the DC is a separate,
independent Tendermint network. Each node of a given network should exist on a
separate instance (as in a VM or docker container). The nodes of a given
Tendermint network must be able to communicate with each other via Tendermint's
peer-to-peer layer. Additionally, each node provides an RPC interface
which clients use to submit transactions and query the state of the chain.

```mermaid
flowchart TD
    subgraph BVC0
    direction LR
    B0N0[N0] --- B0N1
    B0N1[N1] --- B0N2
    B0N2[N2] --- B0N0
    end

    subgraph DC
    direction LR
    DN0[N0] --- DN1
    DN1[N1] --- DN2
    DN2[N2] --- DN0
    end

    subgraph BVC1
    direction LR
    B1N0[N0] --- B1N1
    B1N1[N1] --- B1N2
    B1N2[N2] --- B1N0
    end

    BVC0 --> DC
    BVC1 --> DC
```
