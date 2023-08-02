# Deploy-Nethermind-and-Lodestar

Nethermind is an Execution Layer Client for Ethereum while Lodestar is a Consensus Layer Client for Ethereum.
This repo is just me chronicling my attempt at deploying both blockchain clients.

## Step 1 - Install Nethermind Client on Ubuntu 22.04 LTS from Digital Ocean

* ```sudo apt update```
* ```sudo add-apt-repository ppa:nethermindeth/nethermind```
* ```sudo apt install nethermind```
* ```nethermind --version```

  <img width="609" alt="Nethermind version" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/0d6791a3-39a6-480c-9dd2-cca5579e4d29">

## Step 2 - Configure JSON-RPC API

* ```openssl rand -hex 32 | tr -d "\n" > "/tmp/jwtsecret"```

  <img width="783" alt="neth jwtsecret" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/754cd97f-a442-49fc-942e-a5f5fd2bed12">


## Step 3 - Install and Run Lodestar Client (this required installing git, docker and docker-compose)

* ```docker --version```

  <img width="229" alt="Neth docker version" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/894c7514-c6d5-4e4d-99de-db5053a9c4d2">

* ```docker-compose --version```
  
  <img width="278" alt="Neth docker-compose version" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/f7e88d53-b845-4313-8997-049ea26a5e4b">

* ```docker pull docker pull chainsafe/lodestar```

  <img width="840" alt="Neth docker ps" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/266252ce-6212-4a0a-a884-81da05b95a4c">

* ```git clone https://github.com/ChainSafe/lodestar-quickstart.git```
* ```cd lodestar-quickstart```
  
* I chose to run the node on the sepolia network, so I had to edit the sepolia.vars file and inserted the jwtsecret code as shown

  <img width="937" alt="neth jwtsecret edit" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/6673b2b3-953d-4f2d-86a3-45d911ed6b00">

   
* ```./setup.sh --dataDir --elClient nethermind --network sepolia --justCL --skipImagePull```
* ```./setup.sh --dataDir sepolia-data --elClient nethermind --network sepolia --justCL --skipImagePull --detached```

<img width="945" alt="Neth CL client lodestar running" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/0c0a7ac2-f08a-4feb-ab6e-af6232c8a9b4">

<img width="846" alt="Neth docker ps running" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/133c1615-922f-47f0-8341-aa9e25c25dcd">

## Step 4 - Run Nethermind (Execution Client)
* ```Nethermind.Runner --config sepolia``` # I got an error that i could not immediately resolve, so i decided to document my progress and try again later.
<img width="366" alt="Neth runner" src="https://github.com/Osinachi-Uro/Deploy-Nethermind-and-Lodestar/assets/83463641/064372d5-512f-4b89-ace5-209d60edecb5">


# References
  * https://hackmd.io/@philknows/rJegZyH9q#Update-Ubuntu-Server
  * https://hackmd.io/@philknows/rk5cDvKmK
  * https://docs.nethermind.io/nethermind/first-steps-with-nethermind/running-nethermind-post-merge
  * https://chainsafe.github.io/lodestar/install/docker/
