# Tinycoin

This project is created to learn blockchain by creating a small blockchain and it's own coin. 

# Current stable versions

[![Alt v1.6](https://img.shields.io/badge/release--1.6-ok-green.svg)](https://github.com/prakashpandey/tinycoin/releases/tag/1.6)  [![Alt v1.5](https://img.shields.io/badge/release--1.5-ok-green.svg)](https://github.com/prakashpandey/tinycoin/releases/tag/1.5)  [![Alt v1.2](https://img.shields.io/badge/release--1.2-ok-green.svg)](https://github.com/prakashpandey/tinycoin/releases/tag/v1.2)

To find the latest version please go to the `VERSION` file present at project's base directory 

# Prerequisite

- Python >= 3.6 

If you are running other python versions, this project can be ported to other python versions with small syntax changes.

# How to run?

### 1. I am lazy, I want to setup very fast(docker way)

- Pull the docker image: 

`sudo docker pull prakashpandey/tinycoin:1.6`

- Run the docker image: 

`sudo docker run -p 5000:5000 -d prakashpandey/tinycoin:1.6`

That's it. You have successfully installed the `tinycoin` docker image.

Note: Instead of version `1.6` you can also use version `latest` but it may not be stable one.
      To find the latest version please go to the `VERSION` file present at project's base directory

### 2. I am a hacker, I will setup from scratch

- `git clone https://github.com/prakashpandey/tinycoin`

- `cd tinycoin`

- `pip3 install -r requirements.txt` or `pip install -r requirements.txt` based on your `pip` version


#### '.*NIX' based systems

- `./start.sh`

Note: If your environment uses `python` instead of `python3` then edit the `start.sh` script.

#### Windows system

- set `HOST`, `PORT`, `PEERS` and `MINER_ADDRESS` environment variables. 
  Follow `Configuration` section for more details.

- python src/app.py

By default the application will run on port `5000`


# Configuration

Open file `start.sh`. 
You can set the values of following environment variables according to your needs.

- `HOST="http://127.0.0.1"`

- `PORT=5000`

- `PEERS="http://192.168.1.11:5000,http://192.168.1.12:5000"`

- `MINER_ADDRESS="ppdpp-dvfgf-fredgdsdf-gdsfgsd-35vr433-ee2eass4d"`


# How to build your own tinycoin docker image(Optional)

If you are intrested in building your own docker image please read this section otherwise you can skip this.

 - clone project: `git clone https://github.com/prakashpandey/tinycoin`

- `cd tinycoin`

- build docker image: `sudo docker build -t username/repo-name:tag .`

#### Some helpful docker commands(Optional)

- List all docker images: `sudo docker image ls`

- List all docker containers: `sudo docker container ls`


# Create local test network

Blockchain is all about distribute network where one connect with different `peers` and exchange data on regular bases.
During developement, you will probabily not have a group of distributed peers with whome you may want to connect and exchange
data.

To solve this problem, `testing.sh` script will help you run multiple blockchain instance on different `ports` on the same machine. Open the file `testing.sh` and edit it according to your needs.

# API'S

#### 1. Get miner address

- `Method = Get`

- `Url = localhost:5000/get_miner_address`

- API response `Returns miner address`

#### 2. Update miner address

- `Method = Post`
- `Url = 127.0.0.1:5000/update_miner_address`
- Body 
    ```
        {
            "miner_address": "ppdpp-dvfgf-fredgdsdf-gdsfgsd-35vr433-ee2eass4d"
        }
    ```
- Headers: `Content-Type=application/json`
- API response `Successfully updated miner address` or `Can not update miner_address as valid miner address is not found`

#### 3. Append peers

 Append peers to existing `peer list`

- `Method = Post`
- `Url = 127.0.0.1:5000/append_peers`
- Body 
    ```
        [
            "http://192.168.1.11:5000",
            "http://192.168.1.12:5000"
        ]
    ```
- Headers: `Content-Type=application/json`
- API response `Peer list updated` or `Failed while adding peer/peers. Error[empty peer list received]`

#### 4. Add peers

 Override the existing peers list with new `given peers` list.

- `Method = Post`
- `Url = 127.0.0.1:5000/add_peers`
- Body 
    ```
        [
            "http://192.168.1.11:5000",
            "http://192.168.1.12:5000"
        ]
    ```
- Headers: `Content-Type=application/json`
- API response `Peer list updated` or `Failed while adding peer/peers. Error[empty peer list received]`

#### 5. Create a transaction

- `Method = Post`
- `Url = 127.0.0.1:5000/transaction`
- Body 
    ```
        {
            "from": "71238uqirbfh894-random-public-key-a-alkjdflakjfewn204ij",
            "to": "ppdpp-dvfgf-fredgdsdf-gdsfgsd-35vr433-ee2eass4d",
            "amount": 2
        }
    ```
- Headers: `Content-Type=application/json`
- API response `Transaction submission successful` or `Transaction unsuccessful`

##### 6. Start mining

- `Method = Get`

- `Url = localhost:5000/mine`

- API response `Mined block in JSON format`

#### 7. Get blocks

- `Method = Get`

- `Url = localhost:5000/blocks`

- API response `Blockchain in JSON format`

#### 8. Consensus

- `Method = Get`

- `Url = localhost:5000/consensus`

- API response `Consensus successfully done`

##### 9. Get peers of a node

- `Method = Get`

- `Url = localhost:5000/peers`

- API response `["http://127.0.0.1:5001", "http://127.0.0.1:5002"]`

#### 10. Connect to all peers of peers

- `Method = Get`

- `Url = localhost:5000/connect_to_peers_of_peers`

- API response `["http://127.0.0.1:5002", "http://127.0.0.1:5000"]`

# What more can be done?

The only aim creating this project is to learn and explore about blockchain.
Currently the consensus and proof of work algorithms are very simple. There is scope of improving these algorithm.

##### Future updates

- A wallet client 

- Update proof of work and consensus algorithm

- A valid miner address validater

# Project Screenshot 

![Screenshot](media/screenshot-1.png)

# Resource
This learning project is created just for learning and based on open blog articles on internet.

# LICENSE

GPL V3, please visit [LICENSE](LICENSE.md) for more information.

