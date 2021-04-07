# Creating & Running a Proof of Authority Blockchain

Proof of Authority (PoA) algorithm is used for private/test blockchain networks. This method requires pre-approval of account addresses that can approve transactions

## Steps to Create a PoA Blockchain
___
1. Create accounts for two nodes using directories using the geth application and save node account addresses for use later
    * ./geth --datadir node 1 new
    * ./geth --datadir node 2 new
2. Create private network and intialize genesis block
    * Open a terminal window, navigate to the blockchain-tools folder:
    * ./puppeth
    * Type name for network
    * Type 2 to pick Configure new genesis option, then 1 to create new genesis from scratch
    ![](Screenshots/dogenet_setup.png)
    * Type 2 to choose Proof of Authority
    * Paste both node account addresses to seal and again to pre-fund
    * Choose no pre-funding to keep genesis block clean
    * Complete rest of prompts and specify unique chain/network ID
    ![](Screenshots/dogenet_genesis.png)
    * Export genesis configuration as json file
    ![](Screenshots/dogenet_config_export.png)
3. With genesis block created, initalize nodes with genesis json file
    * ./geth --datadir node1 init dogenet.json
    * ./geth --datadir node2 init dogenet.json
4. Run the nodes to begin mining blocks
    * ./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock
    * ./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
5. Open MyCrypto app and click Change Network at the bottom left
![](Screenshots/mycrypto.png)
    * Click "Add custom node" and select custom in the network column
    * Type ETH in the Currency box.
    * In the Chain ID box, type the chain id from genesis creation.
    * In the URL box type: http://127.0.0.1:8545.
    * Save & Use custom node
![](Screenshots/my_crypto_node_config.png)
6. After connecting to custom node, login wallet, using keystore file from node1
![](Screenshots/keystore.png)
7. Send transaction to node 2's address
![](Screenshots/transaction.png)
8. Check Transaction Status when green push message pops up to confirm transaction
![](Screenshots/dogenet_test_transaction.png)





