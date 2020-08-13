# The Blockchain Ecosystem
- Permissioned blockchain architectures of Hyperledger
- Blockchain as a service by MS Azure
- Dapp Platforms like Augur And Grid+
- Alternative decentralization models like IPFS and Hashgraph
## Hyperledger
There are several use cases for permissioned blockchains e.g. not all transactions are relevant for all participants. One of the most popular permissioned blockchains is the Hyperledger framework by Linux foundation. So far five frameworks emerged from the Hyperledger framework: Fabric, Sawtooth, Indy, Iroha, and Burrow. Currnetly only Fabric 1.0 made it into production state. 
In contrast to coin applications there is no cryptocurrency in hyperledger, hypeledger only applys to incorporate buisness logic. In a permissioned blockchain unknown peers cannot join or leave freely. It is meant for the user in B2B or B2C applications and therefore assumes a certain relationship to be in place. The consensus algorithm ist not PoW (proof-of-Work) but PBFT (Practical Byzantine Fault Tolerance).

## Fabric Model & Functions
The Fabric Model constist of the following items:
1. Transaction
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
7. Identity: participating entites should have verifyable identities like a X.509-certificate. the identity determines the role and the access they have on the blockchain
8. Membership: A trusted Membership Service Provider (MSP) managers memberships and roles. The MSP manges the issuance of X.509-certificates via intemediate and root-certificate authority
9. Consensus Mechanism: Agreement on the next block of the transaction to be added to the chain. This includes validation and verification mechanisms. Depending on the case a round robin or PBFT mechanism may be applied. If there is a potential for a malicious transaction even a PoW mechanism may be applied as consesus model.
In the Fabric framework multiple coexisting blockains (business networks) exist. Interactions between different chains (buiseness networks) are established via confidential smart contracts. E.g. a smart contract may connect the Financial Market Network with the Global Trade Network for a given transaction. Fabriuc model provides the following key features:
- Distributed Ledger Technology
- Confidentiality & Privacy (permissioning)
- Segregation (Channels,Identity)
- Efficiency as peer nodes may operate in parallel (validation, odering, commitment)
- Chaincode

## Development of Hyperledger Fabric Application
The building blocks of Hyperledger Fabric are the following:
- Yeoman Skeleton code
- .cto file: class definitions for assets, participants, and transactions
- .js file: transaction functions
- .acl: access control rules
The composer tool packages these items into a deployable business network archive (.bna).

### Composer 
[Composer Demo](assets/Composer-Demo.pdf)

## Microsoft Azure

## Dapp Platforms
[Augur](https://medium.com/@AugurProject/the-augur-white-paper-a-decentralized-oracle-and-prediction-market-platform-ed8907401c48) is a blockchain implementation of prediciton markets. Key elements of Augur
End-to-End Prediction Marketplace, Trading Platform, Crowd Reporting Process, Reputation System, Oracle generation, Blockchain/SC, robust Algorithms.
Grid+ is an example of distributed energy resuorces (DER)

## Consensus Mechanisms
The consesus problem is referring to the general agreement full nodes need to reach about the next block to be added to the chain. It is thus a core component of the blockchain protocol. All kinds of consensus mechanisms have their advantages and drwabacks. For example the puplar PoW consensus mechanism for BTC (Metropolis) is computation intensive and consumes an enormous amount of energy, in turn it provides a high level of security and thus trust.

### Proof of Work
Compute the has of the block header elements (fixed) and a nonce (variable): 
~~~
H = hash(header,nonce)
if H <= 2^128 (BTC)/ if H F(difficulty) (Eth) 
else change nonce; rpeat
~~~
In case of BTC H <= 2^128 (BTC) menas the leading 128 positions have to be equal to zero. Ethereum metropolis uses a less energy consuming memory based proof of work

### Proof of Stake
PoS ([Youtube Explanation](https://www.youtube.com/watch?v=DqtzxJP6Y9k)) involves the one single full node with the highest balance (or rpound robin amongst the nodes with highest stakes) to add the next block. since its stake is highest it has the least incentive to compromise the network and force a hard fork. Ethereum is gradually moving towards a PoS consensus mechanism, as a consequence the miner fee has been reduced from 5 to 3 Ether per mined block.

### PBFT: Practical Byzantine Fault Tolerance
The Algorithm is proven to tolerate random or Byzantine node failures including potentially malicious nodes. In a nutshel for PBFT nodes vote to elect a leader, that adds the next block to the chain. PBFT is popular in permissioned networks like Hyperledger Fabric. A more advanced verions of PBFT is Asynchronous Byzantine Fault Tolerance (ABFT) also known as Hashgraph. 

## Scalability 
There are different techniques avalible to make DLTs more scalable in terms of transactions per second. An popular on-chain method is to increase the block size. An off-chain method is to maintain state channels of sub networks that can transact faster (e.g. Raiden Network). Sharding and Parallel processing may also serve scalability.

## Privacy
Data access privileges (Create, Read, Update) can be used to add basic privacy to permissioned networks. Confidentiality can be achieved by encrypting or obfuscate data on the chain. An example of a blind bidding process featured by obfuscation goes as follows:
~~~
blindedBid = keccack(bid,fake,secret);
~~~

## IPFS: Interplanetary file system
In contrast to a cnetralized name space like http family. IPFS is a decentalized model for file transfer. The central concepts of IPFS are:
1. A global distributed file system
2. Content based ideintification using secure hash and resolving location using disributed hash table (DHT)
3. Block exchanges abesd on Bittorrent P2P file distribution
4. Incentivizing block echange using Bitswap protocol
5. Merkle DAG (Directed Acyclic Graph) version based organization of file (like Git)
6. Self-certification of storage node servers
A files location is determined form the DHT, where the holding node is identified. Nodes are identified by hashes of the public key. Once the node is identified the P2P transfer via Bittorrent takes place. In contrast to centralized systems a file is not identified by its location, but by its unique identifier created from its content. To resolve the location you send the hashed identifier though the network, on successful response you access the file P2P.
Each node is incentivised to exchange files through the bitswap protocol. In short every node has a 'have' and 'want' list that it can 'trade' on which results in some form of credit or debit balance.
Merkle Directed Acyclic Graph takes care of verisions of a file and makes sure no duplicates are on the network.
IPFS may provide a large scale storage for data related to a blockchain where only the metadata is stored on the blockchain.

[IPFS Exploration Video](https://www.youtube.com/watch?v=8CMxDNuuAiQ)
Steps to install and run loacal
~~~
Download go-ipfs
tar xvfz <tarfile>
cd go-ipfs
./install.sh //install
ipfs init //initialize an details
ipfs add <file-to-be-added> // has is created
ipfs cat <hash-of-the-file-added>
~~~
To run an online version do:
~~~
ipfs deamon // expose the file system to the external world
Go to Browser:
https://gateway.ipfs.io/ipfs/<hash-of-the-file-added>
Web UI:
localhost:5001/webui
~~~

## Hashgraph
Reaching consesus is still the key point in a blockchain. The confirmation fo BTC transaction takes about 8 minutes and consumes about 250 kwh of energy. Hashgrap tries to get around these issues by achieving the following:
- Fairness in terms of transaction ordering
- Eventual Consistency 100%
- Low latency
- Minimal power consumption
- Byzantine Fault Proof
Hashgraph orders transactions in a decentralized network. Building blocks of the hashgraph are:
- Events
- Transactions
- Directed acyclic graph
- Witness
- Famous witness
- Not Famous Witness
- Round: Round created, Round received
- Consensus by voting
- Gossip protocol
- Voting
A graph is a combination of vertices and nodes. A hashgraph incorporates an additional dimension of time. A node of the hasgraph is an event and the transmission of an event represents an edge. This tramsission is called gossip as it is a transfer from one node to another. Gossip transmission is based on rounds.
Every event has on sender participant and one receiver participant. An event consist of an Event Id, the hash of the parent, hash of the other parent (sender) and the payload containing the time ordered transactions. The first event created by a participant in a round is called a witness, as it represents the witness to the state of the graph. Based on whether these event are seen by subsequent event or not a witness may become famous or non-famous. Every event has an associated value roudCreated (1= first round). Depending on how gosspis are transmited over rounds they may become seen or strongly seen (resulting in famous and non famous witnesses), which enables the voting process over rounds.

Psuedo algorithm for Hashgraph:
~~~
loop {
	new event created;
	
	divideRounds; // creates next round if conditions ar met, every memeber of a round should have a witness in that ro
	
	decideFame; // determine if the winesses of the previous rounds are famous
	
	findEventOrder; // after fame is determined, Events are Ordered by assigning roundReceived and timeStamp
	
	// consensus ordering of events, resulting in the ordering of transactions
}
~~~

Hashgraph Consensus Layer runs on the TC/IP layer of the internet. On the top of that layer modules like crypotcurrencies, file systems, and evms are running. On the top of these layer modules a set of APIs is running. 
Reading
[Hashgraph Consensus: Detailed Examples](https://www.swirlds.com/downloads/SWIRLDS-TR-2016-02.pdf)
[What Is Hedera Hashgraph?](https://www.youtube.com/watch?v=MzWiiOLv96I)
[ Hashgraph wants to give you the benefits of blockchain without the limitations](https://techcrunch.com/2018/03/13/hashgraph-wants-to-give-you-the-benefits-of-blockchain-without-the-limitations/)
[Demystifying Hashgraph: Benefits and Challenges](https://hackernoon.com/demystifying-hashgraph-benefits-and-challenges-d605e5c0cee5)
[Hedera Hashgraph Thinks It Can One-Up Bitcoin And Ethereum With Faster Transactions](https://www.forbes.com/sites/jeffkauflin/2018/03/13/hedera-hashgraph-thinks-it-can-one-up-bitcoin-and-ethereum-with-faster-transactions/#5feba94aabcb)
[What is Hashgraph and how will it replace the Blockchain?!](https://www.youtube.com/watch?v=SPdUAw-Fpco)
