# Nano and Nano Fork Nodes Documentation

## Introduction

The Node that keeps track of the Nano or Banano Block Lattice

## Prerequisites

Before running the application, please ensure the follow prerequisites are met:

1. **Docker**:

   - Docker engine installed and running on your system
   - https://docs.docker.com/engine/install/ubuntu/
   - Docker network has been created with `docker network create node-net`

2. **Hosts File**:

   - Update the Host Machines Hosts File with `sudo nano /etc/hosts`
   - Add `127.0.0.1 <container-name>`

5. (OPTIONAL) **Data Configuration**

    - Copy data.ldb to ./data/<node-data-dir>
    - `sudo scp -r ./data.ldb <user>@<local-ip>:<workspace-dir>/data/<node-data-dir>/`
    - (Optional) Copy node_id_private.key to ./data/<node-data-dir>
    - `sudo scp -r ./node_id_private.key <user>@<local-ip>:<workspace-dir>/data/<node-data-dir>/`
    - Copy wallets.ldb to ./data/<node-data-dir>
    - `sudo scp -r ./wallets.ldb <user>@<local-ip>:<workspace-dir>/data/<node-data-dir>/`

6. (OPTIONAL) **RPC Commands**

    - Port Forward
    - `ssh -L <port>:<container-name>:<port> <server-user>@<server-ip>`
    - Confirm block count
    - `curl -X POST http://<container-name>:<port> -H "Content-Type: application/json" -d '{"action":"block_count"}'`

7. **File and Former Permissions Updated**:

   - Docker may not be able to write to your volume by default
   - `sudo chown -R 1000:1000 -R <workspace-dir>`

## Instructions

To run the application, navigate to the root of the project directory and execute `docker compose up -d`