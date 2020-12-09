Akash Challenge Stage 3, Challenge 5





It's now week two of the Challenge 2 process, and it's pretty much the same as the previous challenge, this time deploying an RPC node. This challenge has 200 AKTs.





## Node where edgenet-2 is deployed



deployment-2-2 will deploy akash on another network, download deployment-2-2.yaml



```
wget ttps://raw.githubusercontent.com/ovrclk/docs/ac011af1802a7c5fc7bb90d979c4f4877eaa24e1/testnet-challenges/deploy-2-2.yaml
```

Follow the previous process to deploy SDL and output json to submit.

If you can't connect to the original RPC node, you can replace it with the following one. AKASH_NODE=" [https://akash.rpc.best:443"](https://akash.rpc.best:443"/)





## Send a transaction by deploying node's RPC

In .bashrc, add TESTNET_NODE, the value is the RPC interface of the node you deployed above



```
TESTNET_NODE="RPC interface of the node you deployed above" # Use the official RPC if it doesn't start http://147.75.47.235:26657
```



The private key is common, collect coins from the original wallet address https://akash.vitwit.com/faucet

For transfer instructions, note that meme is used to record remarks and you need to fill in your invitation code. Please make sure it is not empty.







```
akash \
  --node "$TESTNET_NODE" \
  --chain-id akash-edgenet-2 \
  --keyring-backend "$KEYRING_BACKEND" \
  --memo "$CODE" \
  --fees 4000uakt \
  tx send "$KEY_NAME" akash1vl3gun7p8y4ttzajrtyevdy5sa2tjz3a29zuah 1000000uakt
  
  
```



After the transfer is complete, you can use the following command to view the transaction





```
akash query tx [txhash output above] --node "$TESTNET_NODE" --chain-id akash-edgenet-2

```







**That's it, it's easy, now go ahead and try it and complete your own Akash mission.**











**To make it easier for beginners to complete the challenges, you can also refer to the following.**







### Installations:

- git clone https://github.com/blurtbuzz/Akash-Challenges.git
- cd Akash-Challenges
- . ./setup.sh

### Setup Wallet:

- export KEY_NAME="ANY_KEY_NAME"
- export KEYRING_BACKEND="os"
- export ACCOUNT_ADDRESS="$(akash keys show $KEY_NAME -a)"

### Deploy Your App:

- cd
- cd ecosystem

- git remote add upstream https://github.com/ovrclk/ecosystem.git
- git fetch upstream
- git pull upstream master

- curl -s https://raw.githubusercontent.com/ovrclk/docs/ac011af1802a7c5fc7bb90d979c4f4877eaa24e1/testnet-challenges/deploy-2-2.yaml > deploy.yml

- akash tx deployment create deploy.yml --from $KEY_NAME --node $AKASH_NODE --chain-id $AKASH_CHAIN_ID -y

- akash query market lease list --owner $ACCOUNT_ADDRESS --node $AKASH_NODE --state active

  - Wait for your Lease

  leases:

  - lease_id: dseq: "47714" gseq: 1 oseq: 1 owner: akash1nyxtwy6y0crnvrfmctfjyaljzu8y4xc46398ah provider: akash174hxdpuxsuys9qkauaf57ym5j8dm4secnz6jd7 price: amount: "43" denom: uakt state: active pagination: next_key: null total: "0"

- export DSEQ=GENERATED_VALUE_FROM_ABOVE

- export GSEQ=GENERATED_VALUE_FROM_ABOVE

- export OSEQ=GENERATED_VALUE_FROM_ABOVE

- export OWNER=GENERATED_VALUE_FROM_ABOVE

- export PROVIDER=GENERATED_VALUE_FROM_ABOVE

- Go to https://app.akash.network/

- Go to Earn Token Rewards and copy the Participant Code

- export CODE=YOUR_PARTICIPANT_CODE

- akash query market lease get --dseq $DSEQ --gseq $GSEQ --oseq $OSEQ --provider $PROVIDER --owner $ACCOUNT_ADDRESS --node $AKASH_NODE -o json > akashian/phase3/challenge5/$CODE.json

- Commit your change and make a pull request











For more information about Akash, please use the following links to learn more.





Official Website: https://akash.network/?lang=zh-hans  



Twitter: https://twitter.com/akashnet_   



Telegram: https://t.me/AkashNW    



  