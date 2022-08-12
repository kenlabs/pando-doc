See [Pando API document](https://pando-api.kencloud.com/swagger/doc) for more details.
Or check [Pando API Specification](https://pando-api.kencloud.com/swagger/specs)

See [graphql api documentation](https://pando-graphql.kencloud.com/) to query metadata/snapshot status and details.

Pando integrates redoc style documentation, visit `http://127.0.0.1:9000/swagger/doc` for API documentation,
or check `http://127.0.0.1:9000/swagger/specs` for swagger 2.0 specification.

## /pando/health
Check if Pando is alive
```shell
./pando-client -a http://127.0.0.1:9000 pando info

{
 "code": 200,
 "message": "alive",
 "Data": null
}
```
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

## /pando/subscribe
Let Pando subscribe a topic with provider to start metadata synchronization
```shell
./pando-client -a http://127.0.0.1:9000 pando subscribe --provider-peerid 12D3KooWSS3sEujyAXB9SWUvVtQZmxH6vTi9NitqaaRQoUjeEk3M

{
 "code": 200,
 "message": "subscribe success",
 "Data": null
}

```

## /provider/register
Provider should be registered before using Pando service
```shell
./pando-client -a http://127.0.0.1:9000 provider register \
  --peer-id 12D3KooWBckWLKiYoUX4k3HTrbrSe4DD5SPNTKgP6vKTva1NaRkJ \
  --private-key CAESQLypOCKYR7HGwVl4ngNhEqMZ7opchNOUA4Qc1QDpxsARGr2pWUgkXFXKU27TgzIHXqw0tXaUVx2GIbUuLitq22c= \
  --addresses /ip4/127.0.0.1/tcp/9999

{
 "code": 200,
 "message": "register success",
 "Data": null
}

```

to generate an envelop-data only, run:
```shell
./pando-client -a http://127.0.0.1:9000 provider register \
  --only-envelop \
  --peer-id 12D3KooWBckWLKiYoUX4k3HTrbrSe4DD5SPNTKgP6vKTva1NaRkJ \
  --private-key CAESQLypOCKYR7HGwVl4ngNhEqMZ7opchNOUA4Qc1QDpxsARGr2pWUgkXFXKU27TgzIHXqw0tXaUVx2GIbUuLitq22c= \
  --addresses /ip4/127.0.0.1/tcp/9999
  
envelop data saved at ./envelop.data
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
