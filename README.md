TrickboyToken
TrickboyToken is a simple ERC20 token implementation using OpenZeppelin's ERC20 contract. This token is called "Trickboy" with a symbol "TBT".

Features
ERC20 Compliance: TrickboyToken adheres to the ERC20 standard, ensuring compatibility with a wide range of wallets, exchanges, and other tools.
Ownership: The contract defines an owner who has exclusive rights to mint new tokens.
Minting: The owner can mint new tokens to any address.
Transfers: Users can transfer tokens to other addresses.
Getting Started
Prerequisites
Solidity 0.8.20
OpenZeppelin Contracts
Installing
Clone the repository:

sh
Copy code
git clone https://github.com/your-repository/trickboytoken.git
cd trickboytoken
Install dependencies:
Ensure you have the necessary dependencies installed:

sh
Copy code
npm install @openzeppelin/contracts
Compile the contract:
Use your preferred Solidity development environment to compile the contract. For example, with Truffle:

sh
Copy code
truffle compile
Deployment
Deploy the contract to your desired Ethereum network:

Migration Script:
Create a migration script (e.g., 2_deploy_contracts.js) to deploy the contract:

js
Copy code
const TrickboyToken = artifacts.require("TrickboyToken");

module.exports = function(deployer) {
  deployer.deploy(TrickboyToken);
};
Deploy:
Run the deployment:

sh
Copy code
truffle migrate --network <network>
Usage
Contract Address
After deployment, note the contract address for interacting with the token.

Interacting with the Token
You can interact with the token using various Ethereum tools and libraries (e.g., Web3.js, Ethers.js). Below are some basic operations:

Minting Tokens
Only the owner can mint new tokens:

js
Copy code
const trickboyToken = await TrickboyToken.deployed();
await trickboyToken.mint(recipientAddress, amount, { from: ownerAddress });
Transferring Tokens
Any user can transfer tokens to another address:

js
Copy code
await trickboyToken.transfer(toAddress, amount, { from: fromAddress });
Contract Details
State Variables
owner: The address of the contract owner.
_totalSupply: The total supply of the token.
Constructor
solidity
Copy code
constructor() ERC20("Trickboy", "TBT") {
    owner = msg.sender;
    _mint(msg.sender, 1000000 * 10 ** decimals());
    _totalSupply = 1000000 * 10 ** decimals();
}
The constructor initializes the token with the name "Trickboy" and symbol "TBT". It also sets the deployer as the owner and mints an initial supply of 1,000,000 TBT to the owner.

Functions
mint(address _to, uint256 _amount): Allows the owner to mint new tokens.

solidity
Copy code
function mint(address _to, uint256 _amount) public returns (bool success) {
    require(msg.sender == owner, "No other than Trickboy can mint tokens");
    _mint(_to, _amount);
    _totalSupply += _amount;
    return true;
}
transfer(address _to, uint256 _value): Transfers tokens to another address.

solidity
Copy code
function transfer(address _to, uint256 _value) public override returns (bool success) {
    _transfer(msg.sender, _to, _value);
    return true;
}
License
This project is licensed under the MIT License - see the LICENSE file for details.
