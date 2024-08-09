**INTRODUCTION :**
This is a Solidity contract which defines a basic token contract named MyToken with functionalities for minting and burning tokens.

****DESCRIPTION:****
This Solidity contract defines a token named `MyToken` with the following features:
The contract is licensed under the MIT license.

- Token name: "Token_META"
- Token abbreviation: "Token_MTA"
- Total supply initialized to 0
- Mapping to store token balances for each address
- `mint` function to create new tokens and assign them to an address
- `burn` function to reduce the total supply and burn tokens from an address if the balance is sufficient

**Executing program:**
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
