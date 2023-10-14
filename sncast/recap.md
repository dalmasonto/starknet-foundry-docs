# Using Starknet Foundry to interact with Starknet Smart contracts
- Create an account using sncast

    ```sh
    sncast --url http://localhost:5050/rpc account create --name account_name --class-hash predeployed-hash
    ```

- Add funds to the newly created account using the mint url `http://localhost:5050/mint`

    ```curl
    curl -d '{"amount":8646000000000, "address":"0x6a8fe2f52c64693b0e0a9998f0ca18db9f6dd56ac3e1ea02105ea3ade84cbbf"}' -H "Content-Type: application/json" -X POST http://127.0.0.1:5050/mint
    ```

- Deploy the account

    ```sh
    sncast --url http://localhost:5050/rpc account deploy --name account_name --max-fee max_fee 
    ```

- Declare smart contract

    ```sh
    sncast --profile account_name declare --contract-name ContractName 
    ```

- Deploy smart contract

     ```sh
    sncast --profile account_name deploy --class-hash generated_by_declare_command
    ```

- Interact with the deployed contract

    Create a default profile

    ```sh
    sncast call --contract-address ContractAddress --function FuncToCall --calldata [CALLDATA]
    ```

    ```sh
    sncast invoke --contract-address ContractAddress --function FuncToCall --calldata [CALLDATA]
    ```