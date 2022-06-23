# chainlink-dash
Chainlink node setup tool for Dash Platform data


## Setup

#### Requirements
- node v16+
- docker v20.10.12+
- docker-compose v1.29.2+

### Setup Chainlink Node

```
git clone https://github.com/mayoreee/chainlink-dash.git
```
```
cd chainlink-dash
```
```
npm run setup
```

Note: To stop the node, simply use `npm run stop`. Restart the node with `npm run start`.


## Connect Chainlink Node to Dash Platform Data

### Step 1: Login to Chainlink Operator
Open `localhost:6688` in your browser. You should see the Chainlink Operator login page.

<img width="527" alt="Screenshot 2022-06-22 at 18 45 25" src="https://user-images.githubusercontent.com/15247893/175103190-335d11ac-ec5f-4e9a-8aff-36ad285d4a32.png">

Login in with the test info below:
```
Email: email@example.com
Password: 123456789
```

### Step 2: Fund Chainlink Operator
Once you've signed in, grab the operator's address (example in screenshot below) and fund it with ETH (Rinkeby testnet). You can get testnet ETH from a Rinkeby faucet [here](https://faucets.chain.link/rinkeby)

<img width="1440" alt="Screenshot 2022-06-22 at 18 51 13" src="https://user-images.githubusercontent.com/15247893/175104812-1040c635-61f2-4100-b03f-2574554274f3.png">

### Step 3: Create a Job for Dash Platform Data
- Click on "New Job". Then, copy and paste the [job spec](https://github.com/mayoreee/chainlink-dash/blob/master/specs/jobSpec.toml)
- Click on "Create Job" to succefully create the job

### Step 4: Get Oracle Authorization for your Chainlink Node
Now, the Chainlink Oracle needs to authorize your node so it can start fulfilling requests!
- Open the Chainlink Oracle contract [here](https://rinkeby.etherscan.io/address/0x7B54593DfE8f6d23D4fe6a7d542889DC61498BE4#writeContract)
- Connect your wallet with Metamask 
  
  _NOTE: Ensure your wallet is set to use Rinkeby network in Metamask_
<img width="741" alt="Screenshot 2022-06-22 at 19 13 43" src="https://user-images.githubusercontent.com/15247893/175108077-7c1dfc18-1731-406e-b6e9-34b325199b43.png">

- Click on `setAuthorizedSenders` and provide your Chainlink Node address. 
  
  _NOTE: Pass the data as an array of strings e.g. ["INSERT_YOUR_NODE_ADDRESS"]_
<img width="1399" alt="Screenshot 2022-06-22 at 19 17 18" src="https://user-images.githubusercontent.com/15247893/175108575-366b3952-6690-446b-81f3-0523d4d9bd45.png">


**_Hurray!! Your Chainlink Node is now ready to access Dash Platform Data!🥳_**



## Usage

To access Dash Platform data on the Ethereum (Rinkeby tesnet) network, do the following:

  _**NOTE: Currently supports `getBestBlockHash` only**_
  
#### Step 1: Get External Job ID
- Open your Chainlink Operator UI in browser. Click "Jobs".
- Copy the External Job ID. See example in the screenshot below:

<img width="1409" alt="Screenshot 2022-06-22 at 19 38 50" src="https://user-images.githubusercontent.com/15247893/175112140-8ffcd074-c781-4b3f-a871-57d337e0e113.png">

#### Step 2: Make Request to Dash Platform
-  Open the DAPIConsumer smart contract [here](https://rinkeby.etherscan.io/address/0xBe794d5Ed3Ccd8352775F13be64554775633c080#writeContract)
-  Click on `requestBestBlockHash`. Pass in the External Job ID as input in the field '_jobId_'. 
   
   NOTE: Ensure you remove any hyphen(-) in your _jobId_ string. See example below:
    
<img width="1389" alt="Screenshot 2022-06-22 at 20 08 08" src="https://user-images.githubusercontent.com/15247893/175117128-913d85f9-4b86-48bc-9d84-e39683bdc2a5.png">


- Click on "Write" to make request

#### Step 3: Get Request data
After making the request, wait for a brief period to allow the Chainlink Oracle contract fulfill the request on chain. Then:
 - Read the DAPIConsumer smart contract [here](https://rinkeby.etherscan.io/address/0xBe794d5Ed3Ccd8352775F13be64554775633c080#readContract)
 - Click on `bestBlockHash` to read the data. See example below:

<img width="1417" alt="Screenshot 2022-06-22 at 19 57 56" src="https://user-images.githubusercontent.com/15247893/175115396-34800ea0-6549-4bd8-99cf-a07d17c2e824.png">

 













