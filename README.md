# SOLIDITY: CREATE A TOKEN

This Solidity program is a simple "Creating a Token" program that demonstrates the basic syntax and functionality of the Solidity programming language.Creating a token using Solidity is a great way to understand smart contracts and blockchain development.

## Description

Creating a token using Solidity involves writing a program (smart contract) on Ethereum blockchain that defines a digital asset. Tokens can represent anything from currency to assets in a decentralized application (dApp). It's like designing and issuing your own digital currency, governed by predefined rules for how it can be used and transferred.

## Getting Started

### Installing

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file

### Executing program
Setup: Install a Solidity development environment. You can use tools like Remix IDE (online) or set up a local development environment with Truffle and Ganache.

Write the Smart Contract: Create a new Solidity file (e.g., MyToken.sol) and define your token contract. 

```
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.0;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount.
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {
    // Public variables
    string public tokenName = "CRAFT";
    string public tokenAbbrv = "CFT";
    uint public totalSupply = 0;

    // Mapping variable 
    mapping(address => uint) public balances;

    // Mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}

```
This Solidity contract provides basic functionality for a token named "CRAFT" (tokenName) with abbreviation "CFT" (tokenAbbrv). It allows minting new tokens to an address and burning tokens from an address, while ensuring that the balance checks are in place to prevent unauthorized token destruction. It's a foundational contract for creating and managing tokens on the Ethereum blockchain.

## Help

Security Considerations: Ensure proper access control mechanisms are in place for functions like mint and burn. Currently, anyone can call these functions which might not be desirable in all scenarios.
Use of require statements is generally good practice to validate inputs and prevent unexpected behavior.
Gas Costs: Operations like increasing totalSupply and modifying mappings (balances) can become expensive in terms of gas fees on Ethereum. Consider gas optimizations where possible, especially if dealing with large-scale token operations.

## Authors
Sannik Chakraborty
sannikchakraborty2004@gmail.com




## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details
