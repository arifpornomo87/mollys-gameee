
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

### Why Access Control Matters

Without proper access control, anyone could call sensitive functions.  

Using modifiers like `onlyOwner` is one of the first security patterns every developer should learn.

### Ownership Best Practices

- Always emit an event when ownership changes
- Check for the zero address
- Consider using OpenZeppelin’s Ownable for production projects

### Understanding Mappings

Mappings are like hash tables.  

They are very useful for associating addresses with values such as balances, allowances, or user data.

### Why Events + State Is Powerful

State variables store the current data.  
Events provide a history of what happened.

Together they make contracts transparent and easy to integrate with frontends.

### require vs assert

- `require` → for input validation and expected conditions  
- `assert` → for internal errors that should never happen  

In most cases, `require` is what you will use.

### Why Modifiers Are Useful

Modifiers make your code cleaner and more secure by avoiding repeated require statements.

They are one of the most important tools in Solidity.

### Common Global Variables

- `msg.sender` → who is calling the function  
- `msg.value` → how much ETH was sent  
- `block.timestamp` → current time  
- `block.number` → current block number  

These are used constantly in smart contracts.

### receive vs fallback

- `receive()` → called when ETH is sent with empty calldata  
- `fallback()` → called when no other function matches  

Both can be marked as payable.

### receive vs fallback

- `receive()` → called when ETH is sent with empty calldata  
- `fallback()` → called when no other function matches  

Both can be marked as payable.

### When to Use receive and fallback

- Use `receive()` if you mainly want to accept plain ETH transfers  
- Use `fallback()` if you also want to handle unknown function calls  

Many contracts implement both.

### Working with Addresses

Addresses are fundamental in Solidity.  

You will use them for owners, users, balances, approvals, and almost every interaction.

### Why Structs Are Useful

Structs help organize complex data.  

They are commonly used for users, orders, proposals, positions, and more.

### Arrays vs Mappings

- **Arrays** → good for lists and iteration  
- **Mappings** → good for fast lookups by key  

Both are used frequently depending on the use case.

### Best Practices with Loops

- Prefer mappings over arrays when you don’t need iteration  
- Limit the maximum size of arrays  
- Avoid loops that grow indefinitely  

### Conditional Logic Tips

Keep conditions clear and simple.  

Complex nested if statements can make the code harder to read and more error-prone.

### Why Use Enums

Enums improve readability and reduce errors compared to using plain numbers for states.

### Interfaces in Practice

You will see interfaces everywhere in DeFi (ERC20, ERC721, routers, oracles, etc.).

Learning them early is very important.

### Why ERC20 Matters

Because it is a standard, any wallet, DEX, or protocol can interact with ERC20 tokens in a predictable way.

This is one of the foundations of DeFi.

### Understanding Allowance

Allowance lets a contract (like a DEX) spend your tokens without taking full control of your wallet.

This is a core mechanism in DeFi.

### Token Metadata

A complete ERC20 usually includes:

- `name`
- `symbol`
- `decimals`
- `totalSupply`

These help wallets display the token correctly.

### ERC20 Learning Summary

You now understand the core structure of a fungible token.

This knowledge is essential for building or interacting with almost any project on Base.

### ERC20 vs ERC721

- **ERC20** → fungible (all tokens are the same)  
- **ERC721** → non-fungible (each token is unique)  

Both standards are widely used on Base.

### NFT Metadata Basics

Most NFTs store a `tokenURI` that points to a JSON file containing:

- name  
- description  
- image  
- attributes  

This metadata can live on IPFS or a server.

### ERC721 Core Functions

Important functions so far:

- `ownerOf`
- `balanceOf`
- `transfer` / `transferFrom`
- `approve`
- `getApproved`
- `tokenURI`

These form the foundation of most NFT contracts.

### NFT Learning Summary

You now understand the core of ERC721:

- Unique token IDs  
- Ownership tracking  
- Transfers and approvals  
- Metadata with tokenURI  
- Burning tokens  

This is a solid foundation for building NFT projects on Base.
