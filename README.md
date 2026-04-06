# UserRegistry-2
UserRegistry.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract UserRegistry {
    struct User {
        string name;
        uint256 age;
        bool isRegistered;
    }

    mapping(address => User) public users;

    function register(string memory _name, uint256 _age) public {
        require(!users[msg.sender].isRegistered, "Already registered");
        users[msg.sender] = User(_name, _age, true);
    }

    function getUser(address _user) public view returns (string memory, uint256) {
        return (users[_user].name, users[_user].age);
    }
}
