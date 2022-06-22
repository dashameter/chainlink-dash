# chainlink-dash
Chainlink node setup tool for Dash Platform


## Setup

#### Requirements
- node v16+
- docker v20+
- docker-compose v1.29+

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


## Connecting to Dash Platform

### Step 1: Login to Chainlink Operator
After setting up the node as described above, open `localhost:6688` in your browser. You should see the Chainlink Operator login page.

<img width="527" alt="Screenshot 2022-06-22 at 18 45 25" src="https://user-images.githubusercontent.com/15247893/175103190-335d11ac-ec5f-4e9a-8aff-36ad285d4a32.png">

Login in with the test info below:
```
Email: email@example.com
Password: 123456789
```









