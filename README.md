

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
   //This function is used to create new tokens and add them to a specified address.
   //which increases the total supply of tokens and adds the specified amount to the balance of the to address.
    function mint(address to, uint amount) external {
        require(msg.sender == Owner, "only the contract  Owner to do this");
        _mint(to, amount);
    }
//This function allows a user to destroy (burn) a specified amount of their own tokens. 
//which is to reduces the total supply of tokens and subtracts the specified amount from the balance of msg.sender (the caller).
    function burn(uint amount) external {
        _burn(msg.sender, amount);
    }
// The transfer function from the ERC20 contract is overridden here, but it simply calls the parent ERC20 contract’s transfer function using super.transfer(to, amount).
//And includes checks like ensuring the sender has enough balance and updating the balances of both the sender and the recipient.
    function transfer(address to, uint256 amount) public override returns (bool) {
        return super.transfer(to, amount);
    }
 //The transferFrom function from the ERC20 contract is overridden here,
//but it simply calls the parent ERC20 contract’s transferFrom function using super.transferFrom(from, to, amount).
    function transferFrom(address from, address to, uint256 amount) public override returns (bool) {
        return super.transferFrom(from, to, amount);
    }
    
}
