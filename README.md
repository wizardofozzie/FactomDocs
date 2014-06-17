NotaryChains
============
*A Highly Sophisticated Notary Service Secured by the Bitcoin Block Chain*

Using Bitcoin to prove the existence of a document (really any digital asset, like a tweet, a web page, a spreadsheet, a security video, a photo, etc.) is a concept that is well known.  (See the references at the end of this document).  And some have even suggested that a service could be created to take a list of signatures, compute a merkle root, place that in the Bitcoin block chain.  This not only provides the same security, but limits the “block chain Pollution” of pushing a hash into the blockchain for every signed document.  There are at least a couple of online websites that provide these services.

NotaryChains provide for simple “proof of existence” entries.  In addition, NotaryChains provide proof of transform.  NotaryChains implement validation scripts that allow for chains of notarized entries.   NotaryChains can be used to implement token systems, asset trading systems, smart contracts, and more.   A federated set of NotaryChain servers provide for real time audits, easy transfer from one NotaryChain server to another, reduced blockchain pollution, and other benefits.

Bitcoin implements a strict, distributed method for the validation of transactions, where anyone can validate each transaction, and the validity of every input into a transaction can be verified.  Because each transaction is authorized via cryptographic signatures, no transaction can be arbitrarily reversed.  Furthermore, the meaning of each transaction is defined as a validation of the input values (amounts of bitcoin) for each transaction.

The Bitcoin protocol is transactionally complete.  In other words, the creation and distribution of Bitcoins through transactions is completely defined within the Bitcoin protocol.  Transactions (which specify movement of bitcoin) and block discovery (which move bitcoin via mining fees and provide block rewards) are the only inputs into the Bitcoin Protocol, and nothing leaves the Bitcoin Protocol.  In other words, the 21 million Bitcoin that will ultimately exist will always and forever exist within the protocol.  (Well, at least until side chains are implemented, which will provide additional movement of Bitcoin in and out of side chains.)

Many different groups are looking to find ways to leverage the Bitcoin approach for managing other sorts of transactions besides tracking bitcoin balances.  For example, the trading of assets such as houses or cars can be done digitally using Bitcoin.  Even the trading of Commodities such as precious metals, futures, or securities might be done via clever encoding and inserting of information into the Bitcoin blockchain.  

Efforts to expand Bitcoin to cover these kinds of trades include Colored Coins,  Mastercoin, and Counterparty.  Others seek to build their own cryptocurrency with a more flexible protocol that can handle trades beyond currency.  These include Namecoin, Ripple, Etherium, BitShares, NXT, and others.  And of course Open Transactions uses Cryptographic signatures and signed receipts and proof of balance for users (i.e. a user does not need the transaction history to prove their balance, just the last receipt). 

A NotaryChain seeks to gain the ability to track assets and implement contracts, while securing the advantage Bitcoin’s security via Bitcoin block chain.  Instead of inserting transactions into the Blockchain (viewed as “Blockchain Pollution” by many), NotaryChains keep most information off blockchain.  Furthermore, the NotaryChain provides a record keeping system that minimizes the information any actor has to maintain to validate their NotaryChains of interest.  In short,   NotaryChains utilize a combination of mathematical proofs and hashes within the NotaryChains, while inserting the least amount of information into Bitcoin block chain.  The goal is to create an system of records whose audit trails can prove the interactions of NotaryChain users.

A user only needs the artifacts of the NotaryChain of interest rather than the full set of NotaryChains maintained by the NotaryChain servers.

Of course, the NotaryChain can notarize documents, providing proof of their existence at a point in time, and validating their construction (any modification will be detected).  In addition, a NotaryChain provides a provable history, a chain of time stamped events, i.e. a series of entries (i.e. a NotaryChain) that proves a series of events occurred.   This allows a NotaryChain to implement smart contracts and even alternate currencies.  All of which can clear instantly (assuming trust in the NotaryChain servers), and within minutes once a notary entry is secured via the Bitcoin Blockchain.

The NotaryChains are maintained on a set of federated, independently controlled NotaryChain servers.  NotaryChains borrows from the concept of Private Chains, and allows for reactive security by limiting the ability of any NotaryChain server to fail to log entries without immediate detection by not only the other NotaryChain servers, but by the users themselves.  And like Open Transactions, all links in a chain are secured with cryptographic signatures; there is no opportunity for a NotaryChain server to insert a bogus transaction. 

Furthermore, a NotaryChain is largely left ignorant of the significance of any transaction.  The management and backing of any NotaryChain is left to the users of the service.  The NotaryChain is an automated, powerless, and disinterested party to the transformations of a particular NotaryChain.

The NotaryChain concept is designed to allow many different protocols and rules to be run in parallel within data structures designed and implemented by its users.  At the same time, the integrity of the system is secured with the Bitcoin block chain.  NotaryChains also limit the amount of “pollution” to the blockchain that would result if the same data and information were encoded into Bitcoin Transactions.  Additionally, the NotaryChain seeks to reduce the overhead of a single blockchain for sets of transactions that have little to do with one another.  In other words, while Bitcoin benefits from thousands of computers holding the full blockchain, many applications simply need to be auditable, with far fewer systems holding the entire Notary History.  Thus NotaryChains significantly reduce the resources required to process transactions while providing nearly instant transaction clearing.  Federated NotaryChain Servers provide for distributing NotaryChain processing, load balancing, real time audits to insure honesty, and redundancy to insure availability.

Initially, NotaryChain servers will provide APIs to query information from the NotaryChain as needed.  Tools for analyzing the NotaryChain and torrents for distributing the NotaryChain will also be provided.  As technologies such as MaidSafe and the Safe Network come online, then NotaryChain data can be published there in a way that insures all the Notary Blocks are available going forward, despite the fate of any particular NotaryChain Server.

Yet even if the data in NotaryChain servers expand to many terabytes in size, the validity of Notary Entries and particular Notary Chains are only going to require a small portion of that data.

# How NotaryChains Work

![Figure 1](images/fig1.png)

*Figure 1: Diagram showing that Notary Blocks are linked together, and the has of each Notary Block is inserted into the Bitcoin Block Chain.*

Notary Chains are held within a series of Notary Blocks.  The contents of the Notary Block is hashed periodically.  And every so often, the last hash of the Notary Block is inserted into the Bitcoin Block Chain, as shown by Figure 1.  That is all NotaryChains insert into the Bitcoin Blockchain.  With the single insertion, the Notary Block can be provably unalterable (as it would break the hash in the Bitcoin Block Chain).  How the Notary Blocks document their inclusion into the Bitcoin BlockChain is discussed in more detail later.

A Notary Block is created after the previous Notary Block has had its last Hash submitted to the Bitcoin BlockChain.  A new Notary Block begins with a Block ID (one greater than the last), and the transaction hash for the six previous Notary Blocks.   We record six transaction hashes since a transaction hash is mailable and could change.  This is to simplify the lookup of Notary Block hashes in the Bitcoin Blockchain. If a blockchain reorganization changes  the transaction hash, that doesn’t remove the Notary Block’s hash from the Bitcoin Blockchain.

![Figure 2](images/fig2.png)

*Figure 2:  Internal structure of a Notary Block.*

As each Notary Entry is submitted, it is added to the Notary Block, and every so often, a running hash is computed that combindes the hash of the new entry with the previous entries, and that hash is added to the Notary Block.  This prevents any modification of Notary Entries once added to the Notary Block, since any modification of a Notary Entry would break the hash of that entry, and all the hashes that follow. 

For Example, Suppose we ad4 8 Entries (A-D).  The Notary Block would look like this:

1. A
2. h(A) 
3. B
4. h( h(2) + h(B) )
5. C
6. h( h(4) + h(C) )
7. D
8. h( h(6) + h(D) )

#A Simple Notary Entry

Any number of Notary entries can be added to a Notary Block, and remain secured by the Bitcoin Blockchain.  This vastly reduces the overhead of notary functions on the Bitcoin Blockchain without significant loss of security for the notary entries themselves.  We will discuss how the Notary Blocks are published in a later section.  But suffice it to say that anyone holding a copy of a Notary Block can prove its validity by simply providing the Bitcoin Transaction holding the block’s hash.  The block could not possibly have been constructed after the fact (as fitting a block’s contents to produce an existing hash is quite out of the question).  The Bitcoin Transaction holding the Notary Block’s hash + a copy of the Notary Block will fix the existence of a document at a point in time, and prove the document has not been altered.

![Figure 3](images/fig3.png)

*Figure 3: Internal structure of a Notary Entry*

Figure 3 shows a simple Notary Entry.  It is a type Entry (denoting a simple entry).  A simple entry has does not receive any validity checking by the NotaryChain server outside of verifying the signatures, if any are provided.  The user provides the entry, structured data, and the signatures (if desired) for the structured data.  If signatures are provided, but do not validate against the structured data provided, then the entry will be rejected. The NotaryChain service adds the entry type and time stamp, and adds the entry to the current Notary Block.

While a user can use the Structured Data section to implement a range of protocols like tokens, smart contracts, smart properties, etc., NotaryChains provide some generic support for these features.  The support for NotaryChains within NotaryChain servers is necessary to make the NotaryChain Servers auditable in real time for many common functions by its users, and by other Federated NotaryChain Servers.   Federated NotaryChain servers provide the redundancy and cross checking required for the security of many applications that may wish to run on top of NotaryChains.


# How to create a Notary Chain

NotaryChains are chains of Notary Entries. A Notary Chain provides the infrastructure for managing smart contracts, token counts, alternative currencies, etc.  

![Figure 4](images/fig4.png)

*Figure 4] Structure of the first link in a Notary Chain, i.e. a chain of Notary entries*

A Start Link begins a Notary Chain.  It looks just like a simple entry, except for its type, and the fact that the Structured Description must include a “VScript” entry.   Many chains could be validated privately.  In other words, the validation rules for the chain can be published (and notarized) and any attempt to fraudulently add links to the chain are invalidated by the rules published by the parties starting the NotaryChain.  In fact, a reference implementation of an application that validates a NotaryChain can be hashed and secured in the Start Link for a NotaryChain. That application in combination with the published rules for the NotaryChain, rather than the NotaryChain server, would be responsible for validating that NotaryChain. 

Still, there is some use in creating an Account NotaryChain supported by NotaryChain servers, if for no other reason that to allow the group purchase of notary entries by customers.   Because of the reduced overhead of NotaryChains, these can be made available at rates far cheaper than Bitcoin Transactions.

An Account NotaryChain is enforced by the NotaryChain Server.  And it serves as an example for creating user defined chains.  The Start Link for an Account Notary Chain looks like this:

```
NE Type: 	Start Link
Structured Description:	{ 	"type" : "NC*account" , 
    "vscript" : "<sig> <pubKey> OP_CHECKSIG"
    "val" : 1000 }
Signature:	<sig1> <sig2> … <sigN>
```


The Validation Script must evaluate to true for any link that would directly follow the Start Link in the NotaryChain.  The NotaryChain script will implement a subset of the operators defined by Bitcoin, and a few additional operators.  For example, there is no need to implement OP_RETURN, as users can add whatever data they wish to Notary Entries.  Also, the NotaryChain will implement a OP_USER.   This operation will return true immediately as far as the NotaryChain servers are concerned.  But any following operations will be defined as the user sees fit.  Thus they can provide an application that follows the rules that user cares to implement.  OP_USER is only allowed in a type USER NotaryChain.

#Creating Links in a NotaryChain

Following the Start Link is a series of Notary Entries of Type Link.

![Figure 5](images/fig5.png)

*Figure 5:  A link in a Notary Chain*

A Notary Link points back to its parent links.  The Validation Script (part of the structured data) must evaluate to true, or the NotaryChain service will not add the link to the Notary Block.  A USER NotaryChain can possibly accept invalid entries, so it is critical for a NotaryChain of type USER to make use of clear NotaryChain rules and perhaps a reference application for entry validation in order to ignore invalid entries.

#NotaryChain Servers

NotaryChain servers are federated under one of the NotaryChain servers, the Master Notary server.  They register their Notary Blocks with the Master Notary server, and validate the other Notary servers.  Payments for Notary services are managed with Notary Chains and accounts are settled by payments that are made periodically.   Payments can be in Bitcoin, various alt currencies, or even traditional currencies (though that is less likely).  Half of a payment for Notary services should go to the Notary Server accepting payment, and the other half distributed to all the Notary servers providing auditing services.

Each Notary Server must provide access to their Notary Blocks to the other Notary Servers as well as to their users and customers.  For now, access can be provided via websites and torrents.  In the future, they can be provided by MaidSafe and the Safe Network. 

#Bibliography

"Bitcoin." / Mailing Lists. Accessed May 27, 2014. http://sourceforge.net/p/bitcoin/mailman/message/32108143/.

"Could the Bitcoin Network Be Used as an Ultrasecure Notary Service?" Computerworld. Accessed May 27, 2014. http://www.computerworld.com/s/article/9239513/Could_the_Bitcoin_network_be_used_as_an_ultrasecure_notary_service_.

"Proof of Existence." Proof of Existence. Accessed May 27, 2014. http://www.proofofexistence.com/.

"Virtual-Notary." Virtual-Notary. Accessed May 27, 2014. http://virtual-notary.org/.
