**Introduction**

Welcome to this tutorial on creating a simple ERC-20 like token in Solidity! Today, we'll be writing a smart contract that implements basic functionalities like minting and burning tokens. Let's get started!

**Setting Up the License and Solidity Version**

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

We start by specifying the license type, which in this case is MIT. This helps in declaring the licensing terms of the contract. Next, we set the Solidity compiler version to 0.8.18 to ensure compatibility and to leverage the features of this specific version.

**Declaring the Contract and Public Variables**

contract MyToken {

    // public variables here
    string public tokenName = "PLUS";
    string public tokenAbbrv = "ULTRA";
    uint public totalSupply = 0;

We declare our contract MyToken. Inside this contract, we define three public variables:

tokenName - Stores the name of our token, "PLUS".
tokenAbbrv - Stores the abbreviation of our token, "ULTRA".
totalSupply - Tracks the total number of tokens in existence, initialized to zero.

**Mapping for Balances**


    // mapping variable here
    mapping(address => uint) public balances;

We use a mapping to associate each address with its token balance. This mapping, balances, links an address to a uint, representing the balance of that address.

**Mint Function**


    // mint function
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

The mint function allows the creation of new tokens. It takes two parameters: an address _address and a value _value. Here's what it does:

Increases the totalSupply by _value.
Increases the balance of _address by _value.
This function effectively adds new tokens to the specified address.

**Burn Function**


    // burn function
    function burn (address _address, uint _value) public {
        require(balances[_address] >= _value, "Balance is not sufficient for burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}

The burn function destroys tokens, effectively reducing the total supply. It also takes two parameters: an address _address and a value _value. The steps it follows are:

Checks if the balance of _address is at least _value using the require statement. If not, it reverts the transaction with an error message.
Decreases the totalSupply by _value.
Decreases the balance of _address by _value.
This function ensures that tokens are only burned if the address has enough balance, maintaining the integrity of the token supply.

**Conclusion**

And that's it! We've successfully created a simple token contract with mint and burn functionalities. The mint function allows for the creation of new tokens, while the burn function ensures tokens can be destroyed, reducing the total supply. This contract provides a foundational understanding of how token contracts work in Solidity.
