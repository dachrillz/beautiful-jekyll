---
layout: post
title: Proof of Work 2
subtitle: Some more notes on Proof Of Work
tags: [Blockchain]
---
In the last post I established proof of work, why we need it and how it works. However I lately learned while writing my own [blockchain](https://github.com/dachrillz/blockchain-implementation), that proof of work is implemented a little bit differently in Bitcoin compared to how I described it in the last post.

The principle is still the same, but the code implementation is a little bit cleaner and it is is super easy to verify that a block is constructed honestly.
## Proof of Work in Python 
This is an excerpt from how I implemented Proof of Work in the blockchain that I am working on currently. The code is kind of ugly at some places, but my blockchain is simply for learning how they work, so we'll live with it:
```python
def hash_cash(block):
    guess = b'\0'
    while not proof_of_work_solved(block):
        block.nonce = guess
        guess = os.urandom(32)
return guess
```
The function hash cash is named after the [scheme](http://www.hashcash.org/) that inspired Proof of Work. This function finds the value that solves proof of work

It does this by simply guessing until the function proof_of_work() returns true. Which looks like this:
```python
def proof_of_work_solved(block):
    solution = block.get_hash().encode()
    difficulty = block.difficulty_target
    return len(str(solution)) <= 78 - difficulty # Since I represent the hash with an integer, 78 is the length of a sha256 as integer.
```
In the last post I said that the solution to proof of work is the string $c$ such that $f(c|s)$ produces some string with as many leading zeroes as defined by the difficulty. $s$ is the information from the block.

The way Bitcoin actually does it is that it that it takes the whole block, hashes it and then checks if that hash has the correct amount of leading zeroes.

This makes it easy to verify for other nodes if a block is valid. Simply hash it and count the amount of leading zeros!

## What does it mean to hash a block?
The official Bitcoin has some way to encode a block. This is called serialization. Serialized objects are easy to send across networks, as they are just a string of data. The very same string can be run through a hash function.

In my implementation I simply take the data that the block contains when it is instanciated as a Python class, and then I hash that. This looks like following:
```python
class Block:
    def __init__(self, version, prev_hash, merkle_root, timestamp, difficulty_target, nonce, transactions):
        self.version = version
        self.prev_hash = prev_hash  # hash of previous block
        self.merkle_root = merkle_root  # @TODO: not sure if needed in prototype
        self.timestamp = timestamp
        self.difficulty_target = difficulty_target
        self.nonce = nonce

        self.transactions = transactions

    def get_hash(self):
        string_to_be_hashed = str(self.version)
        string_to_be_hashed += str(self.prev_hash)
        string_to_be_hashed += str(self.merkle_root)
        string_to_be_hashed += self.timestamp
        string_to_be_hashed += str(self.difficulty_target)
        string_to_be_hashed += str(self.nonce)
        for item in self.transactions:
            string_to_be_hashed += item.as_string()
        ret = str(int.from_bytes(get_sha_256_from_str(string_to_be_hashed), byteorder='big'))
        return ret
```

All parameters are determined by circumstance. For example the version is what it is. The miner can't really decide how the hashes of the transactions will look, and so on. The only variable that a miner can change in a block freely is the nonce. Therefore the nonce is equivalent to the solution to the proof of work described in the previous post.

## A final correction 
Also since a hash is a mathematical function, it returns a mathematical value. Therefore, strictly speaking, the solution to proof of work is not based on the number of leading zeros. It is based on if the value of the hash is smaller than the difficulty, which is also a number. 

Therefore when one prints the hash of a block as a string it is easy to think that the solution is determined by the number of zeros. This is true in my implementation, but in the real implementation the solution is simply the string $c$ such that:

$f(c|s) < difficulty$.

This allows the difficulty scaling to be more sensitive. In my implementation I can only jump orders of magnitude in the difficulty, as it is based on number of leading zeros. In the real implementation the difficulty can be fine tuned up to integer value precision.