# Integrating with PANDO

## As a Provider
Pando uses [go-legs](https://github.com/filecoin-project/go-legs) to synchronize IPLD data from providers.
You can use PANDO client to easily integrate with Pando.
For now, `/pando/v0.0.1` is the topic Pando subscribes to.

### Prerequisite
Pando accepts IPLD data from metadata providers with the following required IPLD children nodes:
1. `Provider String` - provider's peer ID
2. `Signature Bytes` - signature of the IPLD data: sign( bytes(PreviousID) . bytes(Payload) . bytes(Provider)) )
3. `Payload Bytes`   - bytes of your serialized metadata 

and a nullable node:
1. `PreviousID nullable Link_Metadata` - a non null PreviousID will enable a recursive sync by Pando service. With this node, a full sync of linked IPLD data will be guaranteed.

```
Notice that, once PreviousID is absent when there is some previous metadata, Pando makes no guarantee about the state of metadata published, as the recursive sync won't happen in this case.

Make sure you correctly link your chained metadata using PreviousID node.
```

### Integration process
The provider integration is recommended to follow the steps below:

1. Create a provider instance with Pando client, then connect to Pando, initialize a metadata instance and append new metadata if you need.
2. Push the latest metadata instance.

Check out [these examples](https://github.com/kenlabs/pando/tree/main/example) for more details.

## As a Consumer
To fetch metadata/snapshot status and content via GraphQL API, 
[click here to get a try and dig more](https://pando-graphql.kencloud.com/).

Check out [consumer examples](https://github.com/kenlabs/pando/tree/main/example/consumer/dag) on how to consume Pando data.