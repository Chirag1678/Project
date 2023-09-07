# Final-Project

This is a beginner Solidity Smart Contract to demonstrate the basics of Solidity. 

## Description

The contract contains 3 state variables including the Token Name, Token Abbreviation and Token Supply. 

It has a mapping (Adddress => uint) named balances mapping Addresses to their respective balances. 

It also contains 2 functions namely Mint and Burn which work as their name would suggest. Minting increases the total supply as well as the balance of person who runs this function by a certain value passed to the function as a parameter. 

Burn function checks whether the person who run the function has enough tokens and if they do, it reduces that amount of token from that person's balance as well as from the total supply. It utilizes the require keyword which throws an error if the condition is not met.


## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. Go to https://remix.ethereum.org/.

Once you are on the website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Test.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here

    string public tokenName="META";
    string public tokenAbbrv="Mta";

    uint public totalSupply = 0;
    
    // mapping variable here

    mapping(address => uint )public balances;

    // mint function

    function mint (address _address,uint _value) public 
    {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
     function burn (address _address,uint _value) public 
    {
        if(balances[_address] >= _value)
        {
        totalSupply -= _value;
        balances[_address] -= _value;
        }
    }

}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Test.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the mint or burn function. Click on the "MyToken" contract in the left-hand sidebar, and then click on the "mint" function. 

## Help

Make sure to have the compiler option set to 0.8.18 to avoid version depenedency errors. 
```
pragma solidity ^0.8.18
```

## Authors

  
[Chirag]


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
