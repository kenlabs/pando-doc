# Data Query with BSON

PANDO creates index for IPLD data stored and provides HTTP query interface with BSON support. Internally, PANDO uses MongoDB in data indexing, so we can fully use MongoDB query language in searching IPLD data.

PANDO users can make POST request to the endpoint https://pando-api.kencloud.com/metadata/query for data query. The request body conforms to the following format:

```
{
    "ProviderID": <String of provider ID>,
    "BsonQuery": "<String Representation of BSON query object>"
}
```

For example, if we expect to query all the miner locations identified by `miner-location` property, sorting by date in descending order, we can make the API call with following request body:

```
{
    "ProviderID": "12D3KooWJZ5PMWKH5fSbXjBn1cKE87AgVcuvri4mAaWRTUojq2af",
    "BsonQuery": "{\"find\":\"miner-location\", \"sort\":{\"date\":-1}, \"allowDiskUse\":true, \"limit\":1}"
}
```

To learn more on MongoDB query and BSON, please visit official documentation [Explaining BSON with Examples](https://www.mongodb.com/basics/bson).