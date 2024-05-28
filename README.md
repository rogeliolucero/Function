
Types of Functions
Project: Create and Mint Token
For this project, the functionality of the ERC20 standard token by providing additional functions such as minting, burning, and transfer and transferFrom.



CODE
// SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;

//Module3: Types of Functions

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract LuceroToken is ERC20 {

    address public Owner;
    
    constructor() ERC20("Lucero Token", "LT") {
        _mint(msg.sender, 10000 );
        Owner = msg.sender;
    }
    function mint(address to, uint amount) external {
        require(msg.sender == Owner, "only the contract  Owner to do this");
        _mint(to, amount);
    }
    function burn(uint amount) external {
        _burn(msg.sender, amount);
    }
    function transfer(address to, uint256 amount) public override returns (bool) {
        return super.transfer(to, amount);
    }
    function transferFrom(address from, address to, uint256 amount) public override returns (bool) {
        return super.transferFrom(from, to, amount);
    }
    
}


Author
NTC

Rogelio A Lucero Jr.

8215129@ntc.edu.ph

