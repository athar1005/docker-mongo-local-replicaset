# MongoDB Local ReplicaSet

Sometimes you need a replica set in your local environment (perhaps you want to use the oplog or test multi document transactions). But it's somewhat involved to spin up a series of mongo containers and provide the correct configuration. This docker image will create a self-contained 3 node replica set (that is, all three nodes are running in one container).

**THIS IS ONLY USEFUL FOR LOCAL DEVELOPMENT**

## Usage

Based on mongo:4.4.1-bionic. Supports multi document transactions via mongo sessions.

### 1. Pull image
`docker pull athar1005/docker-mongo-local-replicaset`

### 2. Start Container

`docker run -d -p 27001:27001 -p 27002:27002 -p 27003:27003 --name mongo-rs --mount type=volume,source=data,target=/data -e "REPLICA_SET_NAME=rs0" --restart=unless-stopped mongo-rs:4.4.1-bionic`

### 3. Connect using connection string
The connection string would look like `mongodb://127.0.0.1:27001,127.0.0.1:27002,127.0.0.1:27003/db?replicaSet=rs0`


See extended usage info at https://github.com/flqw/docker-mongo-local-replicaset.
