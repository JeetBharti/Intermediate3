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
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20 {
    constructor() ERC20("Jeet Bharti","JBT") {
        _mint(msg.sender, 1000 * 10 ** 18);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}


