# Ethereum: Smart Contracts
## Week 1
Smart Contracts (SC) are the computational feature of the blockchain technology. The term Smart Contract goes back to [Nick Szabo](http://www.alamut.com/subj/economics/nick_szabo/smartContracts.html). Smart contracts on the Ethereum blockchain are implemented in Solidity language. There is an IDE available for Ethereum Solidity called [Remix](https://remix.ethereum.org).
The smart contract lifts the capabilities of a crypto currency beyond the simple transfer of money. This way rules and policies of arbitrary complexity can be introduced.

A smart contract consists of the following building blocks:
-Pragma driective
-Name of the contract
-Data or State Variables defining the state of the contract
-Collection of functions

The SC equivalent of ‚hello world‘
[greeter.sol](https://gist.githubusercontent.com/GianRothfuchs/fcdaddad12a910040897a0382c9a875d/Greeter.sol)

[![](scrnshot1.gif)](scrnshot1.gif)

Compile using Enviornment ‚Java Script VM‘ and Deploy. The compiler creates the follwoing artifacts:
-ABI: Application Binary Interface describes all the functions in the contract
-Contract Bytecode: Bytecode executed during creation of the contract
-WebDeploy script: Eb3 deploy module, containing the script for invoking the SC from a web application (copy/paste to JavaScript console to deploy the SC).
-Gas estimate: estimates of gas required for function call
-Funciton hashes: quick reference to functions
-Instance Bytecode: actual runtime bytecode of the SC
Address of smart contract. Compile Artifacts: Byte Code ABI, function hasehs, gas estim



