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
   
   ![image](https://user-images.githubusercontent.com/106796537/197262211-c82758b3-6349-422d-bca5-c62e032ca372.png)

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
 
      - 1 Gwei = 10^9 wei
      - 1 Ether = 10^18 wei

We learnt about Gas and Gas price. How does Ethereum ensure that the miner is not spending more Gas than required?

The answer is **Gas Limit**. The Gas Limit for a transaction is defined as the maximum amount of Gas required to run a particular transaction. Hence, the `transaction limit = Gas Limit x Gas Price`.

![image](https://user-images.githubusercontent.com/106796537/197263356-ef3bf176-1c2d-4fbb-bf9b-a5e6888174a3.png)


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

1. **Externally Owned Accounts (EOAs)**: These are combinations of public addresses 
and private keys, and there is no code associated with them. You can use these 
accounts to: 
● Send and receive Ether to/from another account, and
● Send transactions to smart contracts.

2. **Contract Accounts (CAs)**: These accounts do not have a corresponding private 
key. These accounts are generated when you deploy your contract on blockchain. 
You will see them referred to as just contracts in many places (instead of contract 
accounts). Some key features of contract (accounts) are as follows:

● They can send and receive Ether just like EOAs.

● Unlike EOAs, they have code associated with them.

● Transactions have to be triggered by an EOA or another contract.

### Structure of Ethereum Accounts

#### Interaction Between Ethereum Accounts

The following points summarise the transactions in Ethereum:

-  An EOA can send messages to other EOAs or to other CAs by creating and 
signing a transaction using its private key. 
-  An EOA can send messages to other EOAs or to other CAs by creating and 
signing a transaction using its private key. 
- But a message from an EOA to a CA activates the CA’s code, allowing it to 
perform various actions (e.g., transfer tokens, write to internal storage, mint 
new tokens, perform some calculation, create new contracts, etc.).
- Unlike EOAs, CAs cannot initiate new transactions on their own.
- Instead, CAs can only fire transactions in response to other transactions that 
they have received (from an EOA or from another CA).
- An action that occurs on the Ethereum blockchain is always set in motion by 
transactions that are fired from EOAs.

In Ethereum, the values of all the accounts are maintained independently by each 
of the nodes inside the network. And they are all maintained logically as a single 
shared state:

   - All of the accounts capture the snapshot of the blockchain at any particular 
point in time and that goes to every block as an entity.
   - Whenever a new block is created, a state root is stored in the header of that 
block.
State root is the Merkle root of all the accounts at that moment. Simply put, 
all the key–value pairs that represent an account together, form a Merkle 
tree is known as state root.
   - This state root is captured by a block at the time of its creation.
   - Any change in the data would lead to the calculation of the Merkle tree all 
over again to match the state root in the block. This is highly impossible, and 
hence the immutability is maintained in the network. Along with state root, 
the transaction root and the receipt root are also used to capture the state 
of the network in every block.
   - By calculating and storing the roots mentioned above, Ethereum captures 
the network state every time a new block is created (state root, transaction 
root and receipt root).


### Transactions in Ethereum

The various components of a transaction, which are as follows : 
   - **nonce** : A count of the number of transactions sent by the sender.
   - **gasPrice** : The number of Wei that the sender is willing to pay per unit of Gas required to execute the transaction.
   - **to** : The address of the recipient. In a contract-creation transaction, an empty value is used.
   - **value** : The amount of Wei to be transferred from the sender to the recipient. In a contract-creating transaction, this value serves as the starting balance within the newly created contract account.
   - **v, r, s** : Used to generate the signature that identifies the sender of the transaction.
   - **init** : An EVM code fragment that is used to initialize the new contract account.
   - **data** : The input data (i.e., parameters) of the message call. Every type of transaction has all the above components.
  
Let’s now look at the different types of transactions in Ethereum.

- **Message Calls** : These are the internal transactions from EOA to CA or from one CA to some other CA. When one contract sends a message to another contract, the associated code that exists on the recipient contract account is executed.
- **Value Transfer** : Transfer from one EOA to another EOA.
- **Contract Creation Calls** : They are initiated by EOAs, and the recipient's address is kept empty. Such transactions create a new contract account and, hence, are used to create and install new Ethereum contracts.

### Block Anatomy

All transactions are grouped together into 'blocks'. A blockchain contains a series of such blocks that are chained together. A block consists of :
      - The block header 
      - The set of transactions included in that block 
      - A set of other block headers for the current block’s ommers.
      
A block header in Ethereum is quite similar to a block’s in Bitcoin, and apart from components like Parent Hash, nonce, Difficulty, mix hash, Timestamp, it also contains Gas used to mine that block and the Gas limit defined for that block.

Every block header also contains three important Trie structures for :
 -  state (state Root): Merkle root of the current state of all the accounts
 -  transactions (transactions Root): Merkle root of all the transactions mined in that block
 -  receipts (receipts Root): Merkle root of the receipts for all the transactions in that block. A receipt is issued by the network/system whenever a transaction is committed; hence, the receipts for all the transactions in the block will form a Merkle tree, and its root is called the receiptsRoot.
 
These three roots together define the state of the Blockchain network at any given time.

Whenever a new block is created,the network state is captured using these three roots. 

Hence, we can say that at the creation of every new block, the network state changes and the new state is defined by state Root, transaction Root and receipts Root at that instance.




