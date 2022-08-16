# Data Types

PANDO is an IPLD database. It accepts IPLD data from metadata providers with the following required IPLD children nodes:
1. `Provider String` - provider's peer ID
2. `Signature Bytes` - signature of the IPLD data: sign( bytes(PreviousID) . bytes(Payload) . bytes(Provider)) )
3. `Payload Bytes`   - bytes of your serialized metadata 