# NFT
NFT (Non-Fungible Tokens) are the unique token whose amount is one, i.e. there can only exists one NFT in a network. The NFTs can be minted only once and amount can only one to prevent duplicacy. 

The NFT is minted similar to the native assets but can has amount as one and minted only once. So first let's talk about the native assets. 
Native assets are simply assets that has: 
1. PolicyID (currency symbol)
2. Name
3. Amount

>The cardano's ada(lovelace) is also one the native assets with name 'lovelace' and importantly PolicyID as '' (empty/nothing).

A transaction can be created which mints the native assets in which we can define a amount , policyID and name. The amount defines the amount of native assets being minted. The amount can be negative values which means destroying the native assets.

As said earlier the NFT is minted similar to native assets, its because the NFT is one special native assets. The NFT has following characteristics:
1. NFT has a unique policyID i.e. unique currency symbol
2. Amount = 1

## Policy
The idea of NFT is minting only once and only once. So, there comes a problem a transaction can be submited any amount of time. NFT's existance can be checked before creating it this can work if the only on transcation could be done in one slot, this is not the case. So, we use concept of unique UTxOs. As the UTxOs are unique the consumption of UTxOs is checked. The reason of UTxOs being unique is fees. UTxOs hash is calculated from the input UTxO, script. So, there will always some changes in input. The transaction can completely identical but input cannot. This makes UTxOs unique.

The specific UTxOs is provied as a parameter to the minting policy of NFT. The policy checks if the transaction consumes this UTxO provided. So, if can be consumed the NFT is created and UTxOs is consumed so that it cannot be consumed again. And if cannot be consumed the NFT does't get created preserving the uniqueness. 