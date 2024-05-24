# Ethereum-Archive-Node-Deployment-Guide
This is a guide on deploying Ethereum Archive node (Execution Client and Consensus Client). We will be using docker. Please note that you only need archive node if you would like to retrieve the old/historical data. Otherwise, you can just deploy and use a full node.

Step 1: <br/>
Please create the instance/cloud in your preferred cloud platform.

Step 2: <br/>
Install docker and docker-compose by running the following command. <br/>
curl -fsSL https://get.docker.com -o get-docker.sh
DRY_RUN=1 sudo sh ./get-docker.sh
sudo apt install docker-compose
sudo usermod -aG docker $USER <br/>

Step 3: <br/>
Now we will proceed to install Execution client and Consensus client. In this guide, we will use Geth as the Execution client and Prysm as the Consensus client.

Please create a folder and create the "docker-compose.yml" and "config.toml". Feel free to use the "docker-compose.yml" and "config.toml" provided.

Please note that we are deploying an archive node so please make sure the "--gcmode" from docker-compose.yml is set as "archive". 

In this guide, we will configure the Geth Garbage Collector to keep the old data. It is possible to create a partial/recent archive node where the node was synced using snap but the state is never pruned. This can be done by changing the "SyncMode" from config.toml to "snap".

Step 4: <br/>
Please run the following command to deploy and start your Ethereum archive node. <br/>
docker-compose up -d <br/>

Since this is an archive node, the syncing process will take up to 3 weeks to complete.
