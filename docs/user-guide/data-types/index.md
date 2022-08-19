# Data Types

PANDO is an IPLD database. It accepts IPLD data from metadata providers with the following required IPLD children nodes:
1. `Provider String` - provider's peer ID
2. `Signature Bytes` - signature of the IPLD data: dagjson.Encode( ipld.Node{PreviousID, Provider, Payload} ).Bytes()
3. `Payload Bytes`   - bytes of your serialized metadata

and a nullable node:
1. `PreviousID nullable Link_Metadata` - a non null PreviousID will enable a recursive sync by Pando service. With this node, a full sync of linked IPLD data will be guaranteed.

```
Notice that, once PreviousID is absent when there is some previous metadata, Pando makes no guarantee about the state of metadata published, as the recursive sync won't happen in this case.

Make sure you correctly link your chained metadata using PreviousID node.
```

IPLD stands for InterPlanetary Linked Data. It is the data model of the content-addressable web, which allows us to treat all hash-linked data structures as subsets of a unified information space, unifying all data models that link data with hashes as instances of IPLD.

IPLD is an ecosystem of formats and data structures for building applications that can be fully decentralized.

The goal of IPLD is to enable decentralized data structures that are universally addressable and linkable, which in turn will enable more decentralized applications. These addressable and linkable data structures will allow us to do for data what URLs and links did for HTML web pages.

To learn more about IPLD, please visit [ipld.io](https://ipld.io/).