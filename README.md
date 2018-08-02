## HL-1

#### Step - 1

+ Create `crypto-config.yaml` file

+ Run `./bin/cryptogen generate --config=./crypto-config.yaml`

+ Make sure `crypto-config` folder is created

#### Step - 2

+ Create `channel-artifacts` directory

+ Run `./bin/configtxgen -profile <PROFILE_NAME> -outputBlock ./channel-artifacts/genesis.block`

   Example `./bin/configtxgen -profile OneOrgOrdererGenesis -outputBlock ./channel-artifacts/genesis.block`

+ Make sure `channel-artifacts/genesis.block` file is created

#### Step - 3

+ Create `configtx.yaml` file

+ Run `export CHANNEL_NAME=<CHANNEL_NAME>  && ./bin/configtxgen -profile <PROFILE_NAME> -outputCreateChannelTx ./channel-artifacts/<FILE_NAME> -channelID $CHANNEL_NAME`

   Example `export CHANNEL_NAME=channelone  && ./bin/configtxgen -profile OneOrgChannel -outputCreateChannelTx ./channel-artifacts/channel.tx -channelID $CHANNEL_NAME`

+ Make sure `channel-artifacts/<FILE_NAME>` file is created

#### Step - 4

+ Run `./bin/configtxgen -profile <PROFILE_NAME> -outputAnchorPeersUpdate ./channel-artifacts/<FILE_NAME> -channelID $CHANNEL_NAME -asOrg <ORG_NAME>`

   Example `./bin/configtxgen -profile OneOrgChannel -outputAnchorPeersUpdate ./channel-artifacts/Org1MSPanchors.tx -channelID $CHANNEL_NAME -asOrg Org1MSP`

+ Make sure `channel-artifacts/<FILE_NAME>` file is created

#### Step - 5

+ Create `docker-compose.yml` file

+ Run `docker-compose -f docker-compose.yml up -d`

+ Verify with `docker ps -a` that all containers are running