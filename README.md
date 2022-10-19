# Ethereum-Fundamentals
In this module of Ethereum Fundamentals, you will learn everything about the Ethereum network. This module is divided into seven section.

### Ethereum Architecture : 

Here you will learn about the basic components of an Ethereum network and a short depiction of how the blocks of the Ethereum network look like.

### Consensus and Forking : 

These relate to the protocols used to come to a consensus in Ethereum and how is it different from Bitcoin. You will also learn about splitting of chains in Ethereum, called forking.

### Transaction Flow and Challenges in Ethereum : 

The flow of any transaction in Ethereum will be explained here. You will come across some challenges of Ethereum network and how the community is trying to solve these challenges.

### Additional Topics : 

More detailed Ethereum topics such as the network block structure, different types of consensus algorithms and some case studies will be discussed.

## Ethereum Architecture
 Let’s quickly go through the concepts that you will be learning in this session:
 
   -   Introduction to Ethereum
   -   Architecture Overview
   -   Ether and Gas
   -   Ethereum Accounts
   -   Structure of Ethereum Accounts
   -   Transactions in Ethereum
   -   Block Anatomy
   -   Etherscan - A Blockchain Explorer
 
Let’s look at them one by one in detail in the following segments

### Introduction to Ethereum

Ethereum was built to overcome several challenges and inefficiencies faced by the Bitcoin blockchain such as:
  - Unlike Bitcoin, whose sole purpose was to transfer a digital cryptocurrency, Ethereum developers wanted to build a blockchain that is not specific to only one purpose and, instead, could be used to build various applications and not just a payments alternative.
  - Ethereum developers also wanted to solve the mining inefficiency of the Bitcoin network. For this, they wanted to move to some other algorithm than Proof of Work (POW). 
  - 'Proof of Stake' (POS) is what Ethereum has built into its architecture to replace Proof of Work. But POS is still not implemented on Ethereum, and research is continuing on how to implement POS on Ethereum. Ethereum still uses POW for mining.
  
Ethereum was developed in 2013 by a 19-year-old college student **Vitolik Buterin** as part of his college summer project. Ethereum raised **USD 18 million** by initial coin offering and, recently, its market capitalization was **USD 70 billion**.

Today, Ethereum hosts more than 90% of the new tokens on its platforms. The point to note here is that Ethereum was the first blockchain in the world to successfully implement the concept of Smart Contracts which allowed users to create distributed apps (Dapps) over Ethereum.

#### What is Ethereum ?

- The Ethereum blockchain is essentially a transaction-based **state machine**. In Computer Science, a state machine refers to something that will read a series of inputs and, based on those inputs, will transition to a new state.
- The Ethereum blockchain starts from the genesis (first) state, and after every transaction, the state of the entire blockchain changes. Unlike Bitcoin, which follows the UTXO model and stores everything on the chain, Ethereum stores all accounts off-chain. 
- This list of all accounts defines the state of Ethereum at that moment. Whenever a transaction occurs between two accounts, the state of those two accounts changes and, hence, the state of the entire list changes. This new state now becomes the current state of the Ethereum. 

The transactions are stored on the blockchain, thus ensuring the immutability of the states of accounts which are stored off-chain. This can be a little confusing at the moment. But don’t worry - we will look into the details of the state transition model at later stages.

### Architecture overview

In the previous segment, you got a brief introduction to Ethereum.thereum is a transaction-based `‘State Transition Machine’`, which changes to a new state with each new transaction. This explanation will get clearer as you learn the architecture of Ethereum.

The Blockchain network can be broadly classified into the following layers:

 - **Storage layer** : Any kind of data created can be stored in a basic file system or a database. Usually, Ethereum uses databases such as LevelDB or RockDB to store the state of the whole network and other data.
 - **Network layer** : Information like transactions are sent from one node to another in a Blockchain network. This can be done using different messaging protocols. In Ethereum, we use a protocol called JSON - RPC to communicate between nodes.
 - **Protocol layer** : Data and network layers are present in any normal network. How do we make out the difference between any network and a Blockchain network? This is defined by the protocol layer. This layer is majorly composed of the consensus protocols of the Blockchain network.
 - **Application layer** : This is the layer which differentiates between Bitcoin and Ethereum. The application layer defines the various kinds of conditions that can be written on top of the three layers for any particular application. It includes smart contracts which define what your application logic can be.
 
  ![image](https://user-images.githubusercontent.com/101723031/196796289-61bf5dc1-cf2d-40a2-950c-d2d47fcda801.png)

### Ether and Gas

To understand Ethereum at a granular level, you need to understand its core components like the network currency, the transaction process, how a block is added to the network and many more. Let’s start by looking at Ether and Gas - the cryptocurrency and transaction cost of the Ethereum network, respectively. Let’s delve deep into the core components: Ether and Gas.

#### Ether 
 - Ether is the currency internal to Ethereum used to pay transaction fees to miners. 
 - Don’t confuse this with rewards and transaction fees. Those are two separate entities.
 - A miner is rewarded when its block gets selected in the blockchain. However, a miner is not only rewarded on mining the block successfully but also receives a transaction fee for each transaction in the block that it mines.
 - Rewards are given by the system or the Blockchain while the transaction fee is paid by the user who performed that transaction.
 - In Ethereum, there is a defined process to calculate the transaction fee. For example, if current Ether reward for mining a block is 2 Ethers. Hence, on mining a block, a miner receives 2 Ethers + the transaction fee for each transaction in the block.

#### Gas
 - The transaction fee is calculated by measuring the amount of computational power spent by a miner in running that particular transaction.
 - These computational cycles are measured in a unit called Gas. In other words, Gas is the unit used to measure the fees required for a computation.
 - For each Gas that the miner spends to run a transaction, it is paid in Ethers. This is called the Gas Price.
 - So, gas price is the number of Ethers paid per unit of Gas spent by the miner for running a transaction. This gas price is paid by the sender of the transaction to the miner. Gas price is measured in the unit Gwei. Just like Bitcoin, Ether also has multiple denominations. The smallest unit in Ether is Wei.
 
        `1 Gwei = 10^9  Wei`
        
        `1 Ether = 10^18 Wei`
 
We learnt about Gas and Gas price. How does Ethereum ensure that the miner is not spending more Gas than required?

The answer is **Gas Limit**. The Gas Limit for a transaction is defined as the maximum amount of Gas required to run a particular transaction. Hence, the `transaction limit = Gas Limit x Gas Price`.

Now, let’s look at how a transaction is processed and how Gas is consumed.
  - Gas price and Gas limit are set by the sender for every transaction.
  - If excess Gas remains, it is returned to the sender.
  - And if all the Gas is consumed before the transaction is completed, then the transaction fails due to the shortage of Gas and no Gas is returned to the sender.
  - Hence, the calculations to gauge how much Gas would be needed for each transaction need to be done correctly, else your transaction would fail and you would also lose the Gas that you sent with the transaction.
  - Gas is not only used to pay for computation steps, it is also used to pay for storage use. So, a sender also needs to pay a fee for storage use.
      
### Ethereum Accounts

Remember you were told how Ethereum is a `state transition machine`. 

Accounts in Ethereum are stored in a global 'shared state' in the form of key-value pairs. The list of all these key-value pairs representing accounts defines the state of Ethereum at that point. 

In a key-value pair, the key is a 20-byte string which is usually the public key of the account. Value, on the other hand, represents the state of the account. Value is a structure with four values: Nonce, StorageRoot (Storage Hash), CodeHash, Balance.

Every Ethereum account has a key which is its 20-byte unique identifier, and the value is a state which consists of four components, which are present regardless of the type of account :

  - Nonce: If the account is an externally owned account, this number represents the number of transactions sent from the account’s address. If the account is a contract account, the nonce is the number of contracts created by the account.
  - Balance: This is the number of Wei owned by an address. There are 10^18 Wei per Ether.
  - StorageRoot (Storage Hash): This is a hash of the root node of a Merkle tree that encodes the hash of the storage contents of an account.
  - codeHash: This is the hash of the EVM (Ethereum Virtual Machine ) code of this account. For contract accounts, this is the code that gets hashed and stored as the codeHash. For externally owned accounts, the codeHash field is the hash of the empty string.

There are two types of accounts in Ethereum : 
  - **Externally Owned Accounts (EOA)**, which are controlled by private keys and have no code associated with them. 
  - **Contract Accounts (CA)**, which are controlled by their contract code and have a code associated with them.
