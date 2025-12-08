# How-to-deploy-in-Remix-
Paste the code above into Remix.
Make sure Solidity compiler >=0.8.20 is selected.
Use the OpenZeppelin import (works directly in Remix online IDE).
Deploy using the constructor:
name = "YourTokenName"
symbol = "YTN"
initialSupply = total supply (in tokens, not wei! The contract multiplies by 10^decimals automatically).
Example:

Deploy with: name = "BaseL2Token", symbol = "BL2", initialSupply = 1000000
Result: Owner (you) gets 1,000,000 tokens (with 18 decimals).
BaseToken.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract BaseToken is ERC20 {
    constructor(
        string memory name, 
        string memory symbol, 
        uint256 initialSupply
    ) ERC20(name, symbol) {
        _mint(msg.sender, initialSupply * (10 ** decimals()));
    }
}
