# HTTP API

PANDO provides a rich set of HTTP API to support all the features. Learn more about the APIs, checking the [official Pando API document](https://pando-api.kencloud.com/swagger/doc).
If you are interested in more details, feel free to check out [Pando API Specification](https://pando-api.kencloud.com/swagger/specs).

See [GraphQL API documentation](https://pando-graphql.kencloud.com/) on how to query metadata/snapshot status and its details.

The following are the most used endpoints with its sample response.

## /pando/info
Show information of Pando server
```shell
./pando-client -a http://127.0.0.1:9000 pando info

{
"code": 200,
"message": "ok",
"Data": {
    "PeerID": "12D3KooWKw5hu5QcbbFuokt3NrYe7gak5kKHzt8h1FJNqByHQ157",
    "APIAddresses": {
        "GRAPHQL_API": "/ip4/1.1.1.1/tcp/8002",
        "GRAPHSYNC_API": "/ip4/1.1.1.1/tcp/8003",
        "HTTP_API": "/ip4/1.1.1.1/tcp/8001"
    }
}
}

```

## /metadata/list
List all cids of metadata snapshots
```shell
./pando-client -a http://127.0.0.1:9000 metadata list

{
 "code": 200,
 "message": "OK",
 "Data": [
  {
   "/": "bafy2bzacea6qqju247jpt3udlzrafiz2zbe6tdgdxv6sm22ysujnynvz2c3uk"
  }
 ]
}
```

## /metadata/snapshot
lookup and show snapshot information by its cid
```shell
./pando-client -a http://127.0.0.1:9000 \
  metadata snapshot \
  --snapshot-cid bafy2bzacea6qqju247jpt3udlzrafiz2zbe6tdgdxv6sm22ysujnynvz2c3uk

{
 "code": 200,
 "message": "metadataSnapshot found",
 "Data": {
  "CreateTime": 1640992855488796000,
  "ExtraInfo": {
   "MultiAddrs": "/ip4/127.0.0.1/tcp/9002 ",
   "PeerID": "12D3KooWDdL1G1osCHaYb27dVFeixDVoTtGJ1FpSdpBYTMcCM6dC"
  },
  "Height": 0,
  "PrevSnapShot": "",
  "Update": {
   "12D3KooWSS3sEujyAXB9SWUvVtQZmxH6vTi9NitqaaRQoUjeEk3M": {
    "Cidlist": [
     {
      "/": "QmPF6SbfekNZBwpP2zH9XbzM84jY44jBNuZUEcETq7tXdX"
     }
    ],
    "LastCommitHeight": 0
   }
  }
 }
}
```

or by snapshot's height
```shell
./pando-client -a http://127.0.0.1:9000 \
  metadata snapshot \
  --snapshot-height 0

{
 "code": 200,
 "message": "metadataSnapshot found",
 "Data": {
  "CreateTime": 1640992855488796000,
  "ExtraInfo": {
   "MultiAddrs": "/ip4/127.0.0.1/tcp/9002 ",
   "PeerID": "12D3KooWDdL1G1osCHaYb27dVFeixDVoTtGJ1FpSdpBYTMcCM6dC"
  },
  "Height": 0,
  "PrevSnapShot": "",
  "Update": {
   "12D3KooWSS3sEujyAXB9SWUvVtQZmxH6vTi9NitqaaRQoUjeEk3M": {
    "Cidlist": [
     {
      "/": "QmPF6SbfekNZBwpP2zH9XbzM84jY44jBNuZUEcETq7tXdX"
     }
    ],
    "LastCommitHeight": 0
   }
  }
 }
}
```