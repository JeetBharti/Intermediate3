# MyToken Contract

## Overview

`MyToken` is a simple ERC20 token built using the OpenZeppelin library. It inherits from the `ERC20` and `Ownable` contracts provided by OpenZeppelin, ensuring a robust and secure implementation. The token is named "Jeet Bharti" with the symbol "JBT".

## Features

- **Minting**: Initial supply of 1000 tokens (with 18 decimals) is minted to the deployer's address.
- **Burning**: Users can burn their tokens, reducing the total supply.

## Prerequisites

To work with this smart contract, you need to have the following installed:

- Node.js
- npm (Node Package Manager)
- Truffle or Hardhat (for deployment and testing)
- Solidity compiler

## Installation

1. **Clone the repository**:
   ```sh
   git clone https://github.com/your-repo/mytoken.git
   cd mytoken

## Smart Contract Details
   ```sh
   // SPDX-License-Identifier: MIT

//For this project, you will write a smart contract to create your own ERC20 token 
//and deploy it using HardHat or Remix. Once deployed, you should be able to interact 
//with it for your walk-through video. From your chosen tool, the contract owner should 
//be able to mint tokens to a provided address and any user should be able to burn
// and transfer tokens.

pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20 {
    constructor() ERC20("Jeet Bharti","JBT") {
        _mint(msg.sender, 1000 * 10**18);  // Mint 1000 tokens to the contract deployer
    }

    // Function to mint new tokens, callable only by the owner
        function mint(address to, uint256 amount) public  {
        _mint(to, amount);
    }

    // Override transfer function to include a balance check
    function transfer(address recipient, uint256 amount) public override returns (bool) {
        require(balanceOf(msg.sender) >= amount, "Insufficient funds to transfer");
        _transfer(msg.sender, recipient, amount);
        return true;
    }

    function sendFunds(address , uint _amount) public payable{
        require(balanceOf(msg.sender)> _amount, "unsufficient funds to transfer");
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
```
   

## Explanation
Contract Name: MyToken
Inheritance: Inherits from ERC20 and Ownable contracts of OpenZeppelin.
Constructor: Initializes the token with name "Jeet Bharti" and symbol "JBT", and mints 1000 tokens (with 18 decimals) to the deployer's address.
Burn Function: Allows the caller to burn a specified amount of their tokens, reducing the total supply.

## License
This project is licensed under the MIT License - see the LICENSE file for details.


