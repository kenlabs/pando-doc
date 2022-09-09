# CLI Reference

## PANDO Server

### $ ./pando-server help
Help information for all the commands and their options

### $ ./pando-server init
Initialize PANDO server and create its configuration file

### $ ./pando-server daemon
Start PANDO server daemon process

| Flag | Type | Description | Default Value |
| --- | --- | --- | --- |
| --account-level | ints | Rank the accounts then set rate limits for them. | [1,10,100,500] |
| --admin-listen-addr | string | Admin server listen address(in multiaddress format, like /ip4/127.0.0.1/tcp/8999). | | /ip4/127.0.0.1/tcp/8999 |
| --backup-apikey | string | Estuary api key used to backup metadata files. | |
| --backup-check-estuary-interval | string | Interval for Pando to check backup deal status in estuary. | 4h0m0s |
| --backup-estuary-gateway | string | Estuary gateway address used to backup metadata files. | https://api.estuary.tech |
| --backup-estuary-interval | string | Interval for Pando to back up car files to estuary. | 24h0m0s |
| --backup-gencar-interval | string | Interval for Pando to generate car files for providers' meta data. | 1m0s |
| --backup-shuttle-gateway | string | Estuary shuttle gateway address used to backup metadata files. | https://shuttle-4.estuary.tech |
| --cachestore-dir | string | Directory of cachestore files. | cachestore |
|  -f, --config-file | string | Load server configuration from a yaml file rather than line flags. | config.yaml |
| --datastore-dir | string | Directory of datastore files. | datastore |
| --datastore-type | string | Datastore type, support levelds only for now. | levelds |
| -p, --disable-speedtest | | Init server configuration without Internet connection speed test. | |
| --discovery-lotus-gateway | string | Lotus gateway address. | https://api.chain.love |
| --discovery-policy-allow | | Discovery allow all origin source host. | true |
| --discovery-policy-trust | | Enable discovery white-list. | true |
| --external-ip | string | Pando public IP address for API serve | unknown |
| --graphql-listen-addr | string | Graphql server listen address(in multiaddress format, like /ip4/0.0.0.0/tcp/9001). | /ip4/0.0.0.0/tcp/9001 |
| -h, --help | | Print the helper info. | |
| --http-listen-addr | string | Http server listen address(in multiaddress format, like /ip4/0.0.0.0/tcp/9000). | /ip4/0.0.0.0/tcp/9000 |
| --log-level | string | Log level of Pando. | debug |
| --metacache | string | Type of metastore, only support mongodb for now | mongodb |
| --metacache-connection-uri | string | Connection URI of metacache | mongodb://52.14.211.248:27018 |
| --p2p-address | string | P2P hosting address(in multiaddress format, like /ip4/0.0.0.0/tcp/9002). | /ip4/0.0.0.0/tcp/9002 |
| --p2p-server-disable | | Disable libp2p server. | |
| -r, --pando-root | string | Pando root directory which stores data and config file. | ~/.pando |
| -c, --print-config | | Print the configuration info. | |
| --profile-listen-addr | string | Profile server listen address(in multiaddress format, like /ip4/0.0.0.0/tcp/9010). | /ip4/0.0.0.0/tcp/9010 |
| --ratelimit-bandwidth | float | Bandwidth of this runtime (unit: Mbps) | 1 |
| --ratelimit-enable | | Enable rate limiter | false |
| --ratelimit-single-dag-size | float | Estimated single DAG size to receive from providers (unit: Mb) | 1 |
| --snapshot-interval | string | interval to generate snapshot for meta. | 60m |
| -v, --version | | Print the version. | |




