# Proof of Authority Development Chain

## Instructions

## Step One:  Install Go Ethereum Tools:

1. Open your browser and navigate to the Go Ethereum Tools download page at https://geth.ethereum.org/downloads/

2. Scroll down to the "Stable Releases" section and proceed depending on your operating system

3. Install the application

4. Open your "Downloads" folder, and you will find a zipped file staring with 'geth-alltools'

5. Decompress and install in a folder called Blockchain-tools

## Step Two:  generate your genesis block:

1. Open a new terminal window. Navigate into the Blockchain-Tools folder located on the Desktop. Run Puppeth using the command ./puppet as pictured

2. Name your network, and select the option to configure a new genesis block. (#2).

3. Then choose the Clique (Proof of Authority) consensus algorithm

4. Paste both account addresses from the first step one at a time into the list of accounts to seal.

5. Paste them again in the list of accounts to pre-fund.

6. Complete the final prompts in the terminal, and choose "Manage existing genesis" from teh main menu

7. Export the genesis configurations. This will fail to create two of the files, but you only need is 'yournetworkname'.json.


## Step Three: start nodes:

1. With the genesis block creation completed, initialize the nodes.
        * `./geth --datadir node1 init 'yournetworkname'.json`
        * `./geth --datadir node2 init 'yournetworkname'.json`

2. Open separate terminal windows for each node, navigate into Blockchain-Tools and run the following commands:
        * `./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock`
        * `./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock`
    Note: only one node needs ‘RPC’ enabled.

After unlocking the accounts and enabling mining, you should see the nodes producing new blocks.

## Step Four: start nodes and add to wallet:

1. Open your MyCrypto app, click “Change Network” located at the bottom left.

2. Fill in the custom network form, including the chain ID. Use ETH as the currency. Use the http://127.0.0.1:8545 as the URL. This is the default RPC port on a local machine.

3. After connecting to the custom network in MyCrypto, select  View & Send option from the left menu pane in MyCrypto

4. Click Keystore file. On the next screen, click Select Wallet File, then navigate to and select the keystore file inside your Node1 directory. Provide your password.

## Step Three: send eth tokens between accounts:

1. In the “To Address” box, type the account address from Node2, then enter the amount of ETH to send.

2. Click "Send Transaction", and confirm by clicking the "Send" button in the pop-up window.

3. Click the Check TX Status when the green message pops up. Click “Check TX Status” to view the status of the transaction.