# The Blockchain Ecosystem
- Permissiond blockchain architectures of Hyperledger
- Blockchain as a service by MS Azure
- Dapp Platforms like Augur And Grid+
- Alternative decentralization models like IPFS and Hashgraph
## Hyperledger
There are several use cases for permissioned blockchains e.g. not all transactions are relevant for all participants. One of the most popular permissioned blockchains is the Hyperledger framework by Linux foundation. So far five frameworks emergerd from the Hyperledger framework: Fabric, Sawtooth, Indy, Iroha, and Burrow. Currnetly only Fabric 1.0 made it into production state. 
In contrast to coin applications there is no cryptocurrency in hyperledger, hypeledger only applys to incorporate buisness logic. In a permissioned blockchain unknown peers cannot join or leave freely. It is meant for the user in B2B or B2C applications and therefore assumes a certain relationship to be in place. The consensus algorithm ist not PoW (proof-of-Work) but PBFT (Practical Byzantine Fault Tolerance).

## Fabric Model & Functions
The Fabric Model constist of the following items:
1. Trnasaction
2. Peers: 
 2.1 Endorsers: receive, validate, and sign transactions
 2.2 Odering Services: collect signed transactions order into blocks and send to committing peers
 2.3 Committing Peers: recieve blocks, validate (e.g. checking doublespending conditions) and commit to the ledger
3. Assets: Tangible Items of value transacted in blockchain (e.g. financial assets, food supply). Assets are represented as Key/Value pairs in JSON or binary format.
4. Chaincode: Are the smart contract equivalent to Ethereum
 4.1 Definition of Assets
 4.2 Provision of functions for operating on assets and changing asset's states
 4.3 Implementation of application specific rules and policies
5. Ledger: Like the Ethereum blockchain it is a tamper-proof record of transactions/state-changes: 
	Key/Value pair - create, update & delete
6. Channels: Privacy and Confidentiality are enforced through the channel concept. Channel defines a single permissiond network of entities with a single ledger. Channel provides a segregated ledger for a set of entities to transact privately. Channel also enables cross-chain chaincode (smart contracts).
7. Identity: participating entites should have verifyable identities like a X.509-cetrificate. the identity determines the role and the access they have on the blockchain
8. Membership: A trusted Membership Service Provider (MSP) managers memberships and roles. The MSP manges the issuance of X.509-certificates via intemediate and root-certificate authority
9. Consensus Mechanism: Agreement on the next block of the transaction to be added to the chain. This includes validation and verification mechanisms. Depending on the case a round robin or PBFT mechanism may be applied. If there is a potential for a malicious transaction even a PoW mechanism may be applied as consesus model.
In the Fabric framework multiple coexisting blockains (business networks) exist. Interactions between different chains (buiseness networks) are established via confidential smart contracts. E.g. a smart contract may connect the Financial Market Network with the Global Trade Network for a given transaction. Fabriuc model provides the following key features:
- Distributed Ledger Technology
- Confidentiality & Privacy (permissioning)
- Segregation (Channels,Identity)
- Efficiency as peer nodes may operate in parallel (validation, odering, commitment)
- Chaincode

## Developemnt of Hyperledger Fabric Application


