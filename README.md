# aztec-prover Usage Guide

## Server Requirements
- It is recommended to use a server with more than **32 CPU cores** and **128GB RAM** for optimal performance.
- The Hetzner AX series is recommended for hosting, but registration can be challenging:
- Use your real physical address during registration.
- Avoid using a VPN.
- Using a domain-based email address (not a generic provider) increases the chance of successful registration.
- You can get €20 by registering with the link [Hetzner](https://hetzner.cloud/?ref=721ngUYJcM8c), and after successful registration, use the code `LTT25` to get another €20.

## System Requirements
- It is recommended to use **Ubuntu OS** and have **Docker** installed. See the [Docker installation guide for Ubuntu](https://docs.docker.com/engine/install/ubuntu/).

## Environment Variable Configuration
Please modify the following variables in the `.env` file as needed:

| Variable                        | Description                                         |
|----------------------------------|-----------------------------------------------------|
| `VERSION`                       | Version                                             |
| `PROVER_AGENT_COUNT`             | Number of agents to start (adjust based on server performance) |
| `P2P_IP`                        | Node IP address                                     |
| `L1_EXECUTION_HOST_URL`             | Sepolia execution layer RPC URL (You can use an endpoint provided by [Ankr](ankr.com))                     |
| `L1_CONSENSUS_HOST_URL`             | Sepolia consensus layer RPC URL (You can use an endpoint from [dRPC](drpc.org), but for better stability, consider running your own Sepolia node)                     |
| `PROVER_PUBLISHER_PRIVATE_KEY`   | Private key                                         |
| `PROVER_PUBLISHER_ADDRESS`       | Address                                             |

> **Note:** If you have an Aztec validator, you can set `PROVER_COORDINATION_NODE_URL` to the validator's RPC address and set `P2P_ENABLED` to `false`.

## Open Port 40400
Make sure port 40400 is open to the public:

```bash
sudo ufw allow 40400
```

## Directory Creation
Before running, create the following directories:

```bash
sudo mkdir -p /data/prover /data/broker
```

## Start the Service
1. Configure the `.env` file.
2. Create the required directories.
3. Open port 40400.
4. Start the service (for example, using Docker Compose):

```bash
docker-compose up -d
```

For further questions, please refer to other project documentation or contact the developers. 