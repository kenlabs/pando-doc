# Configuring PANDO

Pando server supports the three types of configuration resourc: CLI flag, environment variable, and configuration file.` They are prioritized in the following order:
- CLI flag
- environment variable
- config file (yaml file)

## Configuration items list

ConfigFile (string), specify config file name(only name, not path, its parent path is PandoRoot):
- -f, --config-file
- PD_CONFIGFILE
- /

PandoRoot (string), specify pando root directory for config and data persistence:
- -r, --pando-root
- PD_PANDOROOT
- PandoRoot

PandoDisableSpeedTest (bool), disable internet speed test when init config:
- -p, --disable-speedtest
- PD_DISABLESPEEDTEST
- DisableSpeedTest

LogLevel (string, support DEBUG, INFO, WARN, ERROR, DPANIC, PANIC, FATAL), Pando core module log level
- --log-level
- PD_LOGLEVEL
- LogLevel

Identity.PeerID (string), peer ID of Pando
- /
- PD_IDENTITY_PEERID
- Identity.PeerID

Identity.PrivateKey (string), private key of Pando
- /
- PD_IDENTITY_PRIVATEKEY
- Identity.PrivateKey

ServerAddress.HttpAPIListenAddress (string, example: /ip4/127.0.0.1/tcp/9000), http api listen address in multi-address format
- --http-listen-addr
- PD_SERVERADDRESS_HTTPAPILISTENADDRESS
- ServerAddress.HttpAPIListenAddress

ServerAddress.GraphqlListenAddress (string), graphql api listen address in multi-address format
- --graphql-listen-addr
- PD_SERVERADDRESS_GRAPHQLLISTENADDRESS
- ServerAddress.GraphqlListenAddress

ServerAddress.P2PAddress (string), p2p host listen address  in multi-address format
- --p2p-address
- PD_SERVERADDRESS_P2PADDRESS
- ServerAddress.P2PAddress

ServerAddress.ExternalIP (string), public IP of Pando to serve API
- --external-ip
- PD_SERVERADDRESS_EXTERNALIP
- ServerAddress.ExternalIP

DataStore.Type (string), datastore type, support "levelds" only for now
- --datastore-type
- PD_DATASTORE_TYPE
- DataStore.Type

DataStore.Dir (sting), directory stores all the datastore data, its parent dir is PandoRoot
- --datastore-dir
- PD_DATASOTRE_DIR
- DataStore.Dir

Discovery.LotusGateway （string）, lotus gateway address
- --discovery-lotus-gateway
- PD_DISCOVERY_LOTUSGATEWAY
- Discovery.LotusGateway

Discovery.Policy.Allow (bool), allow all origin source host
- --discovery-policy-allow
- PD_DISCOVERY_POLICY_ALLOW
- Discovery.Policy.Allow

Discovery.Policy.Trust (bool), enable discovery white-list
- --discovery-policy-trust
- PD_DISCOVERY_POLICY_TRUST
- Discovery.Policy.Trust

Discovery.PollInterval (string, example: 24h0m0s), discovery poll interval
- /
- PD_DISCOVERY_POLLINTERVAL
- Discovery.PollInterval

Discovery.RediscoverWait (string), re-discovery wait time duration
- /
- PD_DISCOVERY_REDISCOVERYWAIT
- Discovery.RediscoverWait

Discovery.Timeout (stirng), discovery timeout
- /
- PD_DISCOVERY_TIMEOUT
- Discovery.Timeout

AccountLevel.Threshold (string slice), balance bound of provider, 
see details at [rate-limit doc](https://github.com/kenlabs/pando/blob/main/docs/ratelimit.md)
- --account-level
- PD_ACCOUNTLEVEL_THRESHOLD
- AccountLevel.Threshold

RateLimit.Bandwidth (float64), bandwidth of Pando service environment, this value will be filled when you run 
`./pando-server init`
- --ratelimit-bandwidth
- PD_RATELIMIT_BANDWIDTH
- RateLimit.Bandwidth

RateLimit.SingleDAGSize (float64), estimate size of single DAG structure metadata
- --ratelimit-single-dag-size
- PD_RATELIMIT_SINGLEDAGSIZE
- RateLimit.SingleDAGSize

Backup.EstuaryGateway (string), estuary gateway address
- --backup-estuary-gateway
- PD_BACKUP_ESTUARYGATEWAY
- Backup.EstuaryGateway

Backup.ShuttleGateway (string), estuary shuttle gateway address
- --backup-shuttle-dateway
- PD_BACKUP_SHUTTLEGATEWAY
- Backup.ShuttleGateway

Backup.APIKey (string), estuary api key
- --backup-apikey
- PD_BACKUP_APIKEY
- Backup.APIKey