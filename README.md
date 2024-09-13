# Create a Token with Solidity

This Solidity program use some basic concepts of the Solidity programming language such as mappings, variables, functions, and conditional statements. The goal of this program is to implement what we have learned as beginners.

## Description

The `MyToken` contract is an Ethereum token contract written in Solidity. It is simple in nature, allowing you to create and issue custom tokens. This includes creating a new token or interacting with an existing token.

### Key Elements of the Contract:

- **Token Name**: A string variable that holds the name of the token.
- **Token Abbreviation**: A string variable that holds the abbreviation of the specified token.
- **Total Supply**: A `uint256` variable that tracks all available tokens at any time.
- **Balances**: A mapping linking Ethereum addresses with their corresponding token balances.

### Main Features:

1. **Mint**: A function that allows authorized users to create new coins and send them to an Ethereum address. This increases both the recipient’s balance and the overall supply of tokens.
2. **Burn**: A function used by authorized users to remove a portion of coins from circulation. It first checks whether the user has sufficient balance before updating the balance and decreasing the total supply.

## Run the Program

To run this program, you can use [Remix](https://remix.ethereum.org/), an online Solidity IDE.

### Steps:

1. Visit the Remix website.
2. Click the "+" icon in the left sidebar to create a new file.
3. Save the file with a `.sol` extension (e.g., `CreateAToken.sol`).
4. Copy and paste the following code into the file:

    ```
    solidity
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.0;

    contract MyToken {

    // public variables here
    string public tokenName = "Token_META";
    string public tokenAbbrv = "Token_MTA";
    uint public totalSupply = 0;

    // mapping variable here
    mapping (address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    //It helps to burn insufficient balance
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value){ 
        totalSupply -= _value;
        balances[_address] -= _value;
      }
    }
    }
    ```

5. To compile the code, click the "Solidity Compiler" tab in the left sidebar. Ensure the "Compiler" version is set to `0.8.0` (or another compatible version) and click the "Compile `CreateAToken.sol`" button.

6. After compiling, deploy the contract by selecting the "Deploy & Run Transactions" tab in the left sidebar. Choose the `MyToken` contract from the drop-down menu and click the "Deploy" button.

## How to Interact with Contract Functions

- **Mint**: The `mint()` function enables authorized users to create new tokens and distribute them to specific Ethereum addresses. It updates both the recipient’s balance and the total supply of tokens.
- **Burn**: The `burn()` function allows an authorized user to delete tokens. It checks if the user has enough tokens and adjusts both the balance and total supply accordingly.

## Accessing Contract Variables

- **Token Name**: Use the `tokenName` variable to obtain the name of the token.
- **Token Abbreviation**: The `tokenAbbre` variable contains the abbreviation of the token.
- **Total Supply**: The `totalSupply` variable shows how many tokens are currently in circulation.
- **Balance**: The `balances` mapping allows you to check the token balance for a specific Ethereum address.
  
 ## References

This project was inspired by learning resources such as [Sample Readme](https://bit.ly/SampleReadme1).

## Author

Aryan Chaudhary

## License

This project is licensed under the MIT License.
