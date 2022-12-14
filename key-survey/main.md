# A survey of keys & identities used in zero-knowledge applications.

In any shielded asset transfer protocol, a user will have certain information that should be hidden. A secret key known only to the user is the way of achieving this. Broadly speaking, the user can encrypt information it wishes to hide with this secret key. Now let's get more specific and take some caste studies (zkBob, ZCash, Aztec) and study 1) what information the user hides in each of these protocols and 2) how the secret key is generated.

## zkBob
In zkBob, there are three main pieces of user information that should not be leaked:
- [Accounts](https://docs.zkbob.com/implementation/account-and-notes/accounts). Accounts contain information about the user, such as its balance. Account information should only be able to be decrypted by the account owner.
- [Notes](https://docs.zkbob.com/implementation/account-and-notes/notes). Notes represent a transfer between a sender and a receiver. As such, it contains information, such as the transfer amount. Since we want transactions to be private, notes should only be able to be decrypted by the sender and receiver.
- [Addresses](https://docs.zkbob.com/implementation/zkbob-keys/address-derivation). A new private address is generated for every incoming transaction. 

zkBob [secret key](https://docs.zkbob.com/implementation/zkbob-keys) structure.

## [ZCash](https://zips.z.cash/protocol/protocol.pdf)
Similar to zkBob, notes and addreses should be private in ZCash (see pages 12 and 13). The secret key structure is also on page 12.

## Intuition behind zkBob and ZCash secret key structure
It is clear that the zkBob and ZCash secret key structure are very similar. So, let's try to unwrap if there any logical reasons why.

## Aztec
A key difference between Aztec and zkBob/ZCash is that in Aztec, viewing keys don't necessarily have to be derived from spending keys. Many Aztec apps deterministically and separately derive the spending and viewing keys from signed Ethereum messages.
