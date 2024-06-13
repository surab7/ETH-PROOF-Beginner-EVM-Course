// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract SimpleToken {

    // Public variables
    string public name = "Simple Token";
    string public symbol = "STK";
    uint public totalSupply;

    // Mapping for balances
    mapping(address => uint) public balances;

    // Events
    event Transfer(address indexed from, address indexed to, uint value);
    event Mint(address indexed to, uint value);
    event Burn(address indexed from, uint value);

    // Mint function
    function mint(address _to, uint _value) public {
        totalSupply += _value;
        balances[_to] += _value;
        emit Mint(_to, _value);
        emit Transfer(address(0), _to, _value); // Transfer event from zero address to signify minting
    }

    // Burn function
    function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Insufficient balance");
        totalSupply -= _value;
        balances[_from] -= _value;
        emit Burn(_from, _value);
        emit Transfer(_from, address(0), _value); // Transfer event to zero address to signify burning
    }

    // Transfer function
    function transfer(address _to, uint _value) public returns (bool) {
        require(balances[msg.sender] >= _value, "Insufficient balance");
        balances[msg.sender] -= _value;
        balances[_to] += _value;
        emit Transfer(msg.sender, _to, _value);
        return true;
    }
}
