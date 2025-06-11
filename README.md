# Steps to Run an BigGoGet Node

#### Step 1: Set Up a Directory and Download Files

1. Create a new folder where you want to store your BigGoGet node files.
2. Download the BigGoGet Node Client and the genesis file (`bitgoget.json`) and place them in this folder.

#### Step 2: Initialize the Genesis Block and Define the Directory

Run the following command to initialize the genesis block and specify the data directory:

```bash
./geth --datadir data init bitgoget.json
```

This command initializes the data folder (`data`) using the genesis file (`bitgoget.json`).

#### Step 3: Start the Node in Fullsync Mode

To start your node, use the `geth` command:

```bash
./geth --datadir ./data --bootnodes enode://87888bd215d39409936872c87080f8c5f910c0668064c075c2688a2b82ae88f8ecd8d3b8063ed7a4244a36b9e9306e3fa5924f5f0852d672cf33ea85d0e093b6@185.180.220.213:30303,enode://18623ce8c76395bb0d90d49101523ab128e94956eea0b9b3291e87490e88b417ed1478dae36ecb87ad8df4e31ee4fea2be423879a4ba4a93316e411efb417cde@109.236.90.63:30303 --http --http.addr 0.0.0.0 --http.port 8545 --http.api personal,eth,net,web3,miner --http.vhosts "*" --syncmode "full"
```

This starts the node in full synchronization mode.

To enable mining, use the `--mine` flag with additional mining parameters:

```bash
./geth --datadir ./data --bootnodes enode://87888bd215d39409936872c87080f8c5f910c0668064c075c2688a2b82ae88f8ecd8d3b8063ed7a4244a36b9e9306e3fa5924f5f0852d672cf33ea85d0e093b6@185.180.220.213:30303,enode://18623ce8c76395bb0d90d49101523ab128e94956eea0b9b3291e87490e88b417ed1478dae36ecb87ad8df4e31ee4fea2be423879a4ba4a93316e411efb417cde@109.236.90.63:30303 --http --http.addr 0.0.0.0 --http.port 8545 --http.api personal,eth,net,web3,miner --http.vhosts "*" --syncmode "full" --mine --miner.threads=1 --miner.etherbase 0xYourEthereumAddress
```

Replace `0xYourEthereumAddress` with your own Ethereum address to receive mining rewards.

---

### Additional Information

#### Port Configuration for Running an BigGoGet Node

The port settings can be customized to match your network configuration and security preferences.

- **P2P Port (`--port`)**: Used for peer-to-peer networking. In this example, it’s set to `30303`, but any open port not in conflict with other services on your system can be used. Ensure your firewall permits the chosen port.
- **HTTP Port (`--http.port`)**: Enables HTTP-based communication with the node’s API, defaulting to `8545` but customizable to any valid port number. Configure firewall settings accordingly to prevent unauthorized access.
- **WebSocket Port (`--ws.port`)**: Used for real-time WebSocket communication. It often defaults to `8546` but can be modified to any open port. Ensure the port is allowed in the firewall for WebSocket use.

To adjust the ports, use the following syntax:

```bash
--port <your_desired_port> --http.port <your_http_port> --ws.port <your_ws_port>
```

Choosing unique ports outside common ranges can help improve security, though ensure these ports are allowed for connectivity with the BigGoGet network.

- **API Exposure**: Adjust the `--http.api` and `--ws.api` options based on your API exposure needs.
- **Security Considerations**: Configure your firewall and HTTP settings to secure your node, particularly on open networks.

---

### Troubleshooting

- **Genesis File Error**: Verify that the genesis file path is correct during initialization.
- **Connection Issues**: Ensure your firewall settings allow the necessary ports for peer-to-peer connectivity.

---

Enjoy running your BigGoGet node! For further assistance, feel free to open an issue in the official repository.
