
Project Title
Smart Contract Bank

Simple Overview of Use/Purpose
This Solidity smart contract implements a basic banking system where users can deposit and withdraw Ether. It uses interfaces and abstract contracts to structure the code.

Description
The Bank contract allows users to deposit and withdraw Ether. It includes functions to check account balances. The contract implements an interface MyBank and an abstract contract BankBase. The interface defines the main functionalities, and the abstract contract provides basic balance storage and functions.

Getting Started
Installing
Install Remix IDE or any other Solidity development environment.
Create a new file and copy the Bank contract code into it.
How/Where to Download Your Program
The contract code can be directly copied from the provided snippet and pasted into your development environment.
Any Modifications Needed to Be Made to Files/Folders
No modifications are needed to the contract code for basic usage.
Executing Program
How to Run the Program
Open Remix IDE and create a new file named Bank.sol.
Paste the provided contract code into Bank.sol.
Compile the contract using the Solidity compiler version 0.8.26.
Deploy the contract to a local blockchain (e.g., Remix VM) or a testnet (e.g., Ropsten, Rinkeby).
Step-by-Step Bullets
Open Remix IDE.
Create a new file: Bank.sol.
Paste the contract code into Bank.sol.
Select the appropriate compiler version (0.8.26).
Compile the contract.
Deploy the contract using the "Deploy & Run Transactions" tab.
Interact with the deployed contract using the available functions (deposit, withdraw, getBalance).
Code Blocks for Commands
// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

interface MyBank {
    function deposit() external payable;
    function withdraw(uint256 amount) external;
    function getBalance(address account) external view returns(uint256);
}

abstract contract BankBase {
    mapping(address => uint256) internal balances;

    function getBalance(address account) public view virtual returns(uint256) {
        return balances[account];
    }

    function deposit() public virtual payable;
    function withdraw(uint256 amount) public virtual;
}

contract Bank is MyBank, BankBase {
    function deposit() public override(BankBase, MyBank) payable {
        require(msg.value > 0, "Deposit amount must be greater than zero");
        balances[msg.sender] += msg.value;
    }

    function withdraw(uint256 amount) public override(BankBase, MyBank) {
        require(amount <= balances[msg.sender], "Insufficient balance");
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }

    function getBalance(address account) public view override(BankBase, MyBank) returns(uint256) {
        return balances[account];
    }
}

Project Title
Smart Contract Bank

Simple Overview of Use/Purpose
This Solidity smart contract implements a basic banking system where users can deposit and withdraw Ether. It uses interfaces and abstract contracts to structure the code.

Description
The Bank contract allows users to deposit and withdraw Ether. It includes functions to check account balances. The contract implements an interface MyBank and an abstract contract BankBase. The interface defines the main functionalities, and the abstract contract provides basic balance storage and functions.

Getting Started
Installing
Install Remix IDE or any other Solidity development environment.
Create a new file and copy the Bank contract code into it.
How/Where to Download Your Program
The contract code can be directly copied from the provided snippet and pasted into your development environment.
Any Modifications Needed to Be Made to Files/Folders
No modifications are needed to the contract code for basic usage.
Executing Program
How to Run the Program
Open Remix IDE and create a new file named Bank.sol.
Paste the provided contract code into Bank.sol.
Compile the contract using the Solidity compiler version 0.8.26.
Deploy the contract to a local blockchain (e.g., Remix VM) or a testnet (e.g., Ropsten, Rinkeby).
Step-by-Step Bullets
Open Remix IDE.
Create a new file: Bank.sol.
Paste the contract code into Bank.sol.
Select the appropriate compiler version (0.8.26).
Compile the contract.
Deploy the contract using the "Deploy & Run Transactions" tab.
Interact with the deployed contract using the available functions (deposit, withdraw, getBalance).
Code Blocks for Commands
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

interface MyBank {
    function deposit() external payable;
    function withdraw(uint256 amount) external;
    function getBalance(address account) external view returns(uint256);
}

abstract contract BankBase {
    mapping(address => uint256) internal balances;

    function getBalance(address account) public view virtual returns(uint256) {
        return balances[account];
    }

    function deposit() public virtual payable;
    function withdraw(uint256 amount) public virtual;
}

contract Bank is MyBank, BankBase {
    function deposit() public override(BankBase, MyBank) payable {
        require(msg.value > 0, "Deposit amount must be greater than zero");
        balances[msg.sender] += msg.value;
    }

    function withdraw(uint256 amount) public override(BankBase, MyBank) {
        require(amount <= balances[msg.sender], "Insufficient balance");
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }

    function getBalance(address account) public view override(BankBase, MyBank) returns(uint256) {
        return balances[account];
    }
}
Help
Any Advice for Common Problems or Issues
Ensure you are using the correct Solidity compiler version (0.8.26).
Make sure you have sufficient Ether in your account when testing deposits.
Withdrawals can only be made if the balance is sufficient.
Command to Run if Program Contains Helper Info
No additional helper commands are required for this contract.
Authors
Contributors names and contact info:

Raja Kumar:@rajapusaho@gmail.com
License
This project is licensed under the MIT License - see the LICENSE.md file for details
