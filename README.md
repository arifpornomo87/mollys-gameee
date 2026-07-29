# Starting with Base

I'm using this repository to organize everything related to Base — from basic concepts to more advanced topics as I progress.

### Learning Goals

1. Understand how Layer 2 works  
2. Learn the basics of the Base network  
3. Explore tools and resources  
4. Gradually move into practical development  

This repo will document the process.

### First Impressions

Base feels approachable for beginners while still being powerful enough for real applications.  

I’m excited to keep learning and documenting everything here.

### Understanding Public Variables

When a variable is declared as `public`, Solidity automatically creates a getter function for it.

This makes it easy to read data from the contract.

### View vs Pure Functions

- `view` → reads state but doesn’t modify it  
- `pure` → doesn’t read or modify state  

Understanding these helps write more efficient contracts.

### Why Events Are Useful

Events allow applications to react to what happens on-chain without constantly reading the contract state.

They are also cheaper than storing extra data.

### Understanding Constructors

Constructors are optional, but very useful when you want to initialize important values at the moment the contract is created on Base.
