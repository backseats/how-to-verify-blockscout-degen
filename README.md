# How to Verify a Smart Contract on Degen with Foundry/Forge

By [Backseats](https://warpcast.com/backseats)

1. You've developed your contract in Forge already.

2. Now it's time to deploy.

3. Make sure you have your env vars set in your `.env` file and run `source .env` in your terminal to load in the latest env vars.

4. Next, write your script file and run it with

`forge script script/DFSplitter.s.sol:DFSplitterScript --rpc-url $DEGEN_RPC_URL --chain-id 666666666 --private-key $DEGEN_PRIVATE_KEY --broadcast -vvvv`

or more generically:

`forge script script/<script_name>.s.sol:<contract_name> --rpc-url $DEGEN_RPC_URL --chain-id 666666666 --private-key $DEGEN_PRIVATE_KEY --broadcast -vvvv`

5. Now verify it. First, output the verifyme.json file. Your `ETHERSCAN_API_KEY` can be any value. Blockscout just ignores it but Foundry/Forge need it so make sure you have some value in your `.env` file. Could be an empty string.

Then run:

```
forge verify-contract <contract_address> ./src/<contract_file_name>.sol:<contract_name> --etherscan-api-key $ETHERSCAN_API_KEY --show-standard-json-input > verifyme.json
```

6. Next, go to `https://explorer.degen.tips/contract-verification`, enter your contract address which you can find in your terminal logs from the `-vvvv` output. Add in the contract license and the `Verification Method` should be "Solidity (Standard JSON input)"

7. Choose your compiler version (again from the terminal logs)

8. Upload the `verifyme.json` file and submit.

That should verify your contract!
