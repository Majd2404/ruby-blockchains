# ruby-blockchains

# Let's create a blockchain using Ruby

### HASH

SHA-256 (Secure Hash Algorithm 256) is a cryptographic hash function that produces a unique 256-bit (32-byte) hash value for any given input. It is part of the SHA-2 family of hash functions, which were developed by the National Security Agency (NSA) in the early 2000s.

SHA-256 is widely used in a variety of applications, including:

Blockchain technology: SHA-256 is used in blockchain technology to create unique identifiers for blocks and transactions.
SHA-256 is considered to be a very secure hash function, and it is resistant to known attacks. It is also relatively fast and efficient to compute, making it suitable for a wide range of applications.

Digital signatures: SHA-256 can be used to create digital signatures, which are used to verify the authenticity of a message or document.
Password authentication: SHA-256 can be used to store passwords in a secure manner. When a user logs in, their password is hashed using SHA-256 and the hash is compared to the stored hash. If the hashes match, the user is authenticated.
File integrity verification: SHA-256 can be used to verify the integrity of a file. The hash of the file is calculated and stored when the file is created. When the file is later downloaded or opened, the hash is recalculated and compared to the stored hash. If the hashes match, the file is verified to be intact.

### BLOCK

A block in cryptocurrency is a digital record of all transactions that have occurred on a blockchain network in a given period of time. Blocks are added to the blockchain in chronological order, and each block is linked to the previous block using cryptography. This creates a chain of blocks that is very difficult to tamper with, making blockchain technology very secure.

Blocks typically contain the following information:

+ A timestamp indicating the time at which the block was created
+ A reference to the previous block in the chain
+ A list of all transactions that occurred during the block period
+ A cryptographic hash of the block

The cryptographic hash of the block is used to link the block to the previous block in the chain and to ensure that the block has not been tampered with. If a single transaction in the block is changed, the cryptographic hash of the block will also change, making it obvious that the block has been tampered with.

Blocks are created by miners, who are special nodes on the blockchain network that are responsible for verifying and adding new transactions to the blockchain. Miners compete to solve a complex mathematical puzzle in order to create a new block. When a miner solves the puzzle, they are rewarded with cryptocurrency.

Once a new block is created, it is broadcast to the entire blockchain network. All of the nodes on the network then verify the block and add it to their own copy of the blockchain. This process ensures that all of the nodes on the network have a copy of the same blockchain, which makes it very difficult to cheat or tamper with the system.

Blocks are an essential part of blockchain technology. They provide a secure and efficient way to record and verify all transactions that occur on a blockchain network.


To create a crypto block in Ruby, you can use the following code:

```ruby
require 'crypto-ruby'
require 'elliptic-curve'

class CryptoBlock
  attr_accessor :version, :timestamp, :previous_block_hash, :merkle_root, :nonce, :signature

  def initialize(version, timestamp, previous_block_hash, merkle_root, nonce, signature)
    @version = version
    @timestamp = timestamp
    @previous_block_hash = previous_block_hash
    @merkle_root = merkle_root
    @nonce = nonce
    @signature = signature
  end

  def generate_hash
    Crypto.sha256(self.to_json)
  end

  def verify_signature(public_key)
    EllipticCurve::Signature.verify(@signature, self.to_json, public_key)
  end
end

```
To verify a crypto block in Ruby, you can use the following code:

```Ruby
def verify_block(block)
  # Verify that the block has a valid hash
  if block.generate_hash != block.hash
    return false
  end

  # Verify that the block has a valid signature
  if !block.verify_signature(public_key)
    return false
  end

  # The block is valid
  return true
end

```


### Blockchain

Blockchain is a shared, immutable ledger that facilitates the process of recording transactions and tracking assets in a business network. An asset can be tangible (a house, car, cash, land) or intangible (intellectual property, patents, copyrights, branding). Virtually anything of value can be tracked and traded on a blockchain network, reducing risk and cutting costs for all involved.

Here are some examples of how blockchains are being used today:

Cryptocurrencies: Blockchains are used to power cryptocurrencies such as Bitcoin and Ethereum. Cryptocurrencies are digital or virtual tokens that use cryptography to secure their transactions and to control the creation of new units.
Decentralized finance (DeFi): DeFi is a financial system that uses blockchains to provide financial services without the need for intermediaries such as banks. DeFi applications include decentralized exchanges, lending platforms, and insurance platforms.
Non-fungible tokens (NFTs): NFTs are unique digital assets that are stored on blockchains. NFTs can be used to represent ownership of digital items such as artwork, music, and videos.
Supply chain management: Blockchains can be used to track the movement of goods through a supply chain. This can help to improve transparency and efficiency.
Healthcare: Blockchains can be used to store patient records and to track the movement of drugs and medical devices. This can help to improve patient safety and reduce fraud.


Sources:
https://www.ibm.com/topics/blockchain
https://www.futurescope.co/what-is-defi/

### Timestamping

Timestamping in blockchain is the process of recording the date and time of a digital document or event on a blockchain. This provides proof that the document or event existed at a specific time.



Here are some examples of timestamping formats:

YYYY-MM-DD HH:MM:SS: This is the most common timestamping format. It is used by many programming languages and operating systems.
YYYY-MM-DDTHH:MM:SSZ: This is an ISO 8601 timestamping format. It is used by many web services and APIs.
Unix epoch time: This is a timestamping format that represents the number of seconds elapsed since the Unix epoch (January 1, 1970, at 00:00:00 UTC).
RFC 3339: This is a timestamping format that is defined by the Internet Engineering Task Force (IETF). It is used by many email clients and web servers.
Here are some examples of timestamps in each format:

YYYY-MM-DD HH:MM:SS: 2023-11-07 12:00:00

YYYY-MM-DDTHH:MM:SSZ: 2023-11-07T12:00:00Z

Unix epoch time: 1668038400

RFC 3339: 2023-11-07T12:00:00+00:00


### Mining 

In the context of blockchain technology, mining refers to the process by which new transactions are added to the blockchain, and new blocks are created and added to the existing chain. This process is a fundamental part of many blockchain networks, especially those that use a proof-of-work (PoW) consensus algorithm.

Mining is important for several reasons:

+ It secures the blockchain by making it very difficult to tamper with data.
+ It helps to decentralize the blockchain by distributing the power to add new blocks to many different miners.
+ It incentivizes miners to support the network by rewarding them with cryptocurrency.

There are two main types of mining:

+ Proof-of-work (PoW): This is the type of mining that is used by Bitcoin and other early cryptocurrencies. In PoW mining, miners compete to solve complex mathematical problems. The first miner to solve a problem gets to add a new block to the blockchain and is rewarded with cryptocurrency.

+ Proof-of-stake (PoS): This is a newer type of mining that is becoming more popular. In PoS mining, miners are rewarded based on the amount of cryptocurrency that they stake. The more cryptocurrency that a miner stakes, the more likely they are to be selected to add a new block to the blockchain.
