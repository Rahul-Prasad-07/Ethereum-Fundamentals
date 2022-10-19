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
