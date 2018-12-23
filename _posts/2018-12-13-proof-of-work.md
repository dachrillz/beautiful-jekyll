---
layout: post
title: Proof of Work
subtitle: A crucial features that secure the public blockchain
tags: [Blockchain]
---
Blockchain is one of the technologies I am most excited about at this moment. I'm part of the camp that believe that decentralised applications will have a big part to play in the our near future. Without diving too deep into the philosophy and morality of what is possible with blockchains this is my first attempt to really solidify what I know about blockchains on a technical level. I plan to write more and more about the technology and the economical aspects of blockchains in the coming future. Without further ado, here is my first blog post on how the basic hash cash protocol works in the early versions of bitcoin.
# What is proof of work? 
In a way the sole purpose of a blockchain is to transact value from one peer to another. Given that we have a blockchain that works as intended, how do we decide who gets to make a transaction? This decision has to be fully decentralised, as otherwise we need to rely on some central server that dictates whom can conduct information across the blockchain and who can not. This is very anti thetical to what blockchain is supposed to be about, decentralisation. Another way is to simply allow peers to send transactions as they please, no strings attached. With this comes yet another problem. If it were free to send transactions, one peer could send trillions of transactions, effectively using the whole bandwidth of the blockchain to send bogus transactions.

Bitcoin's solution to this is called proof of work. The actors that actually commit transactions to the chain are called miners. They basically scoop up pending transactions, add them to a block and then finally, append that block to the blockchain. End users pay fees to the miners for the service. However a miner is simply software, and were it not for proof of work a miner could spam the network and as a consequence destroy it.

Proof of work is basically; in order to be able to commit the transactions to the chain you have to offer something that is valuable to you. In the case of proof of work this is computational power. This discourages miners that want to simply spam the network as they actually have to conduct work in order to do the spamming. 

# What does proof of work look like? 
Proof of work has to have 2 basic features. First of it has to be a problem that is hard to solve. Secondly it has to be easy to verify that a solution is correct. There are various proof of work schemes that work in different ways. As of this writing however Bitcoin is based on the scheme called [Hashcash](https://en.bitcoin.it/wiki/Hashcash). 

Hashcash is actually a really simple scheme. The hardness of the problem comes from trying to reverse some cryptographic hash function.

Mathematically a cryptographic hash function is simply a highly discontinuous function. This is the reason why they are so hard to reverse. How would you find the inverse of such a function, where there is discontinuity at every point. The only way to find the inverse of a well designed hash function is to brute force it. 

The problem we want to solve in the case of Bitcoin looks like following.

1. Two parameters are given, a string that is information about the blockchain at its current state, as well as a degree of difficulty. Both of these parameters will be explained shortly.
2. We call the given string $s$.
3. The difficulty is simply the number of leading zeroes in the solution string that we call $z$.
4. We take a string $c$ and append it to $s$ like $sc$ and run it trough a cryptographic function $f$ like so $f(sc)$
5. The solution to the problem is the string $c$ that solves $f(sc) = z$. 
6. Note, we do not care about $z$ per se, only that it contains a certain amount of leading zeroes, as defined by the difficulty.

In the case of bitcoin the string $s$ contains information that can help peers determine the integrity of the blockchain up to that block.

The function $f$ is the sha256 hash function applied twice. (Also called sha256-squared)

#Why do we need the difficulty?
The difficulty determines how fast we can solve this problem. The faster we can solve this problem the faster we can create blocks and append them to the blockchain. Various blockchains have different time intervals at when they write new block to the chain. Bitcoin for whatever reason settled for $10$ minutes per block. The reason we need some time between each block is due to the fact that this is a decentralised network, and the nodes need to communicate their states to one another. If the time between blocks is too low then the nodes might fall out of sync, destabilizing the network. Why $10$ minutes was chosen for Bitcoin I do not know. I know that litecoin settled for 2.5 minutes, and that blockchain seems to work fine with such a low time between blocks.

The reason difficulty defines time between blocks is due to the fact that the ability one has to solve the proof of work problem is directly related to how much computing power one has access to. That is if we add more computers that try to solve this problem it will be solved faster. By increasing the number of zeroes that we require in the solution we can control the rate at which the problem is solved.

This way we can dynamically change the difficulty as miners come and go with various computing capabilities in order to keep the time between blocks consistent.

#Why does proof of work create security?
As already mentioned proof of work prevents spam in the network, but there is another aspect to the scheme that secures the network. Many times in cryptography the ability to crack some problem is simply due to the amount of computing power that one is willing to throw at the problem. This is the case for sha1 for example. [It was deemed secure](https://security.googleblog.com/2017/02/announcing-first-sha1-collision.html) until google threw its endless computing capabilities at it. 

The reason why miners spend all this electricity and computing power on solving the proof of work problem is due to the fact that they recieve a reward from constructing that block, as well as all the transaction fees from the transactions inside the block. This proposes a question for anyone with a lot of computing power. Should I attack the bitcoin network, hoping that I can hack it and steal bitcoin from other peers or should I simply try to solve the proof of work problem and get rewards anyway? The first approach will most likely damage the price of bitcoin and make the attack less potent, where as the later one adds computing power to the global computing power pool and thus makes it harder for future attackers to steal the bitcoin that you get as a reward for solving the proof of work problem.

Empirically proof of work has been a major success in the Bitcoin network as no major attack has been able to outcompete the miners that behave honestly with respect to the network.

#The problem with proof of work.
I have not seen any paper written about this but I assume that the difficulty should be directly correlated with the price of bitcoin. This is due to the simple fact that the more profitable bitcoin is the more people should want to mine. If Bitcoin really is to become a well entrenched system of the future, this could mean that it is highly evaluated. This could potentially attract alot of miners with very fast hardware. Imagine if Bitcoin is a large percentage of some large market. At some point major computing firms might find it more profitable to simply mine Bitcoin instead of selling their old services. What I'm trying to say is that as more miners join the race to solve the proof of work problem, the difficulty gets higher and the amount of computing power needed to solve the problem increases dramatically. 

Large amounts of computing power also means large amount of electricity consumption. In the case of Bitcoin the network consumed electricy [comparable to smaller nations states](https://digiconomist.net/bitcoin-energy-consumption). It could be debated whether this is a problem in itself. Of course we want to minimize energy consumption wherever we can, but if proof of work is what secures the network then they energy consumption might not be a problem in itself. For example cars consume an astronomical amount of energy every day, but it is generally concluded that they have benefited mankind as a whole. Instead of banning cars we try to find ways for them to be less pollutant. The same argument can be applied to bitcoin. This problem simply goes away if we can generate energy cheaply and cleanly.

There is another potential solution that has been implemented in some smaller blockchains.

#An alternative to proof of work
Proof of work forces peers that want to contribute to the blockchain to sacrifice something of worth to be able to participate in the network. Proof of work also works as an oracle that randomly selects who gets to write the next block into the blockchain. There are problems with this as well, as the distribution is not uniform, but is biased toward peers that have more computing power than others. I won't go too deeply into this here, but the problem should not be ignored. The problem gets even worse when several miners combine their efforts into [pools](https://www.buybitcoinworldwide.com/mining/pools/) that control large chunks of the total computing power in the network. This way these pools could collude in order to misuse the protocol. For example a majority of these pools could go together and simply ignore all transactions from certain a certain address, thus effectively preventing certain peers from making transactions in the network. Not very decentralised indeed!

Another approach to proof of work is called proof of stake. I will write more about this in another post. My understanding is not very deep of it at this time, but it will be very exciting to see if any of the blockchains can push the proof of stake scheme to the same scale as bitcoin pushed the proof of work scheme. 

Basically proof of stake is that you stake tokens that you own in order to be able to vote for whatever in the blockchain. Most likely one would vote for transactions or who would get to create the next block. This could capture the essentials of the proof of work as well, without the crazy power consumption. The election could be randomized, but tilted in favour of who stakes the most. This encourages owners of some token to take the future construction of blocks seriously since the have "stakes" in the blockchain. 

There are a myriad of problems that comes with proof of stake, such as the [nothing at stake](https://hackernoon.com/thoughts-about-nothing-at-stake-b93b13bb5d6e) problem. I will write more about this in another blog post as I am very curious as to whether this protocol will work as well as the proof of work protocol, in regards to making the network secure as well as incentivizing random people to actually contribute to the well being of the block chain.
