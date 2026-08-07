

# Starting with Base

I'm using this repository to organize everything related to Base — from basic concepts to more advanced topics as I progress.

### Learning Goals

1. Understand how Layer 2 works  
2. Learn the basics of the Base network  
3. Explore tools and resources  
4. Gradually move into practical development  

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

### Paid Mint Best Practices

- Always check `msg.value`
- Add a max supply
- Allow the owner to update the price
- Emit events on mint
- Consider adding a pause function later

### Why Pause Is Important

A pause function is a simple but powerful safety mechanism.  

It allows the owner to stop minting or other actions if something unexpected happens.

### Useful View Functions

View functions are free to call and very helpful for:

- Frontends  
- Explorers  
- Users checking information  

Always try to expose useful data with view functions.

### Batch Mint Considerations

- More convenient for users  
- Uses more gas as quantity increases  
- Always enforce a maximum per transaction  
- Check both payment and max supply carefully  

### Useful NFT Data to Store

Besides ownership, it is common to store:

- Mint timestamp  
- Original minter  
- Token URI  
- Optional attributes or levels  

This makes the NFT more useful and transparent.

### Tracking Provenance

Saving the original minter and mint timestamp helps with:

- Provenance  
- Rarity  
- Future utility (boosts, rewards, etc.)  
- Transparency for collectors

### Dynamic NFT Idea

By adding levels, attributes, or experience, the NFT can evolve over time.

This is a common pattern for gaming and utility NFTs on Base.

### Gamification Ideas

Adding levels and experience opens the door to:

- Game mechanics  
- Rewards based on level  
- Breeding or evolution systems  
- Leaderboards  
- Utility in other contracts  

This makes NFTs much more interactive.

### Metadata Best Practices

- Use a consistent baseURI  
- Prefer IPFS for decentralization  
- Keep metadata immutable when possible  
- Include name, description, image and attributes  

### Improving Standard Compliance

To make the NFT more compatible with the ecosystem, it is recommended to implement:

- ERC165  
- ERC721  
- ERC721Metadata  

This makes the collection work better with wallets and marketplaces.

### Collection Metadata

Just like tokens have metadata, collections usually define:

- Name  
- Symbol  
- Description (off-chain)  
- Image / banner (off-chain)  

These help with discoverability on marketplaces.

### Input Validation Best Practices

Always validate:

- Zero addresses  
- Token existence  
- Ownership  
- Allowances / approvals  
- Array bounds  

Good validation makes contracts much safer.

### Useful Token States

Common states for NFTs:

- Normal  
- Locked  
- Staked  
- Listed for sale  
- In game / in use  

Using an enum makes the code clearer and safer.

### Status Management Summary

By adding statuses you can control:

- Whether a token can be transferred  
- Whether it can be used in a game  
- Whether it is currently staked  

This adds a lot of flexibility to the NFT.

### NFT Staking Basics

Staking NFTs is a very common mechanic used for:

- Earning rewards  
- Access to special features  
- Governance power  
- In-game benefits  

It is a great next step after basic NFT functionality.

### Staking Rewards Summary

You can reward NFT holders based on:

- Time staked  
- Token level / rarity  
- Number of NFTs staked  
- Special attributes  

This creates strong incentives to hold and stake the NFTs.

### Flexible Reward Systems

You can make rewards depend on:

- Time staked  
- NFT level  
- Rarity  
- Number of staked NFTs  
- Special events or seasons  

This keeps the system interesting over time.

### Staking Rules Summary

Useful rules to add to staking systems:

- Minimum staking time  
- Lock periods  
- Early unstake penalties  
- Reward multipliers  
- Maximum number of staked NFTs per user  

These help balance the system.

### Designing Good Staking Incentives

Good staking systems usually combine:

- Rewards for long-term holding  
- Penalties for early exits  
- Extra boosts for higher level / rarer NFTs  
- Clear and transparent rules  

This encourages long-term participation.

### Why Limit Staked NFTs

Setting a maximum number of staked NFTs per user can help:

- Prevent whales from dominating rewards  
- Encourage wider participation  
- Balance the economy of the project  

### Frontend Friendly Design

When designing contracts, think about what the frontend will need:

- Easy way to get user balances  
- List of staked tokens  
- Pending rewards  
- Token stats  

Adding the right view functions and storage makes integration much easier.

### Useful Global Statistics

Interesting stats to expose:

- Total minted  
- Max supply  
- Currently staked  
- Total rewards distributed  
- Number of unique holders  

These help with transparency and dashboards.

### Transparency in Rewards

Tracking total rewards distributed helps with:

- Trust  
- Analytics  
- Understanding the economy of the project  
- Showing the value generated for holders  

### Emergency Controls Summary

Useful emergency features:

- Pause minting  
- Pause staking  
- Pause transfers (in extreme cases)  
- Withdraw funds  

Having these options makes the contract safer to manage.

### Basic Security Habits

- Use `require` generously  
- Protect sensitive functions with modifiers  
- Follow Checks-Effects-Interactions  
- Prefer `call` over `transfer`  
- Add pause functionality  
- Emit events for important changes  

These habits already prevent many common issues.

### Project Progress Note

This repository is documenting the progressive construction of a more complete NFT system on Base, starting from very simple examples and gradually adding real utility features.

### Breeding System Considerations

When designing breeding you should think about:

- Requirements (level, rarity, cooldown)  
- Cost (ETH or tokens)  
- Genetic / attribute inheritance  
- Supply control  
- Cooldowns to avoid inflation  

### Balancing Breeding

To keep the economy healthy you can combine:

- Breeding cost  
- Cooldowns  
- Level requirements  
- Maximum supply  
- Burning of parents (optional)  

Good balancing prevents inflation of the collection.

### On-chain Attributes

Storing attributes on-chain allows:

- Game logic based on stats  
- Rarity calculation  
- Dynamic metadata  
- Verifiable traits  

Note: For real randomness it is better to use Chainlink VRF.

### Using Attributes in Game Logic

Attributes can be used for:

- Combat power  
- Staking multipliers  
- Breeding requirements  
- Access to special features  
- Leaderboards  

They add depth to the NFT system.

### Rarity Systems

Rarity can be determined by:

- On-chain attributes  
- Power score  
- Visual traits (usually off-chain)  
- Special events or limited editions  

On-chain rarity is transparent and verifiable.

### Leaderboard Considerations

On-chain leaderboards are possible but expensive when many users are involved.

Common solutions:
- Keep only Top 10 / Top 100 on-chain
- Calculate scores off-chain and verify on-chain
- Use events for indexing
### Marketplace Basics

A simple marketplace usually needs:

- Listing function  
- Cancel function  
- Buy function  
- Events for listings and sales  
- Handling of payments and ownership transfer  

This is a foundational pattern for NFT trading.

### Marketplace Fee Considerations

- Keep fees reasonable (usually 2-5%)  
- Clearly communicate the fee to users  
- Decide where the fee goes (treasury, rewards, burn, etc.)  
- Emit events for transparency  

### Marketplace Events Summary

Important events for a marketplace:

- `TokenListed`  
- `ListingCancelled`  
- `TokenSold`  

These events make it easy for frontends and indexers to track activity.

### Offers vs Listings

- **Listings** → seller sets the price  
- **Offers** → buyer proposes a price  

Supporting both makes the marketplace more flexible and user-friendly.

### Marketplace Features Summary

Current marketplace features:

- List NFT for sale  
- Cancel listing  
- Buy NFT  
- Make offer  
- Accept offer  
- Cancel offer  
- Marketplace fee  

This is already a solid foundation for a basic NFT marketplace.

### Royalties on NFTs

Royalties allow creators to receive a percentage of secondary sales.

This is a very important feature for sustainable NFT projects.
### Creator Earnings

With royalties, creators can continue earning from secondary market activity.

This is one of the main advantages of NFTs compared to traditional digital assets.
### Project Status

This repository documents the step-by-step construction of a feature-rich NFT system on Base.

It started from very basic concepts and has progressively evolved into a more complete project.

### Ownable in OpenZeppelin

OpenZeppelin’s `Ownable` already includes:

- `owner()`  
- `onlyOwner` modifier  
- `transferOwnership`  
- `renounceOwnership`  

This saves time and reduces errors.

### Useful OpenZeppelin Utilities

Commonly used modules:

- `Ownable`  
- `Pausable`  
- `ReentrancyGuard`  
- `ERC721URIStorage`  
- `ERC721Enumerable`  
- `ERC2981` (royalties)  

These cover most needs of an NFT project.

### OpenZeppelin Royalties Summary

Using ERC2981 from OpenZeppelin gives you:

- Standard royalty support  
- Compatibility with major marketplaces  
- Easy configuration  
- Cleaner and safer code  

### OpenZeppelin Migration Summary

By switching to OpenZeppelin you gain:

- Better security  
- Standard compliance  
- Cleaner code  
- Easier maintenance  
- Ready-made modules for royalties, pausing, ownership, etc.  

This is the recommended path for production-ready contracts on Base.

### Common Mint Restrictions

Useful limits for minting:

- Max supply  
- Max per wallet  
- Max per transaction  
- Mint price  
- Pause functionality  

These help keep the mint fair and controlled.

### Allowlist vs Public Mint

Common flow:

1. Allowlist phase (early supporters)  
2. Public mint phase  

This is a very popular strategy for NFT launches.

### Allowlist Methods Comparison

- **Mapping** → simple but expensive for many users  
- **Merkle Tree** → efficient and scalable  

For most real launches, Merkle proofs are the better choice.

### Reveal Mechanics

Many NFT projects use a two-step process:

1. Mint with hidden metadata (placeholder image)  
2. Reveal the real traits later  

This increases excitement and allows generating traits after the mint.

### Reveal Best Practices

- Use a clear placeholder image  
- Communicate the reveal date  
- Prefer IPFS for metadata  
- Avoid changing metadata after reveal (unless the project is designed to be dynamic)  

### When to Use ERC721Enumerable

Use it when:

- You want an easy way to list tokens on-chain  
- The collection size is not extremely large  
- User experience is more important than gas optimization  

Otherwise, event indexing is often enough.

### Admin Mint vs Public Mint

It is common to have both:

- **Public mint** → for users  
- **Admin/owner mint** → for team, marketing, vault, giveaways, etc.  

Keeping them separate makes the contract clearer.

### Mint Phase Strategy

A common and effective strategy is:

1. Closed  
2. Allowlist / Whitelist  
3. Public  
4. (Optional) Free or bonus phase  

This gives better control and a fairer launch.
### Reserved Supply for Team

```solidity
uint256 public reservedSupply = 50;
uint256 public reservedMinted = 0;

function teamMint(address to, string memory uri) public onlyOwner {
    require(reservedMinted < reservedSupply, "Reserved supply exhausted");
    require(nextTokenId < maxSupply, "Max supply reached");

    uint256 tokenId = nextTokenId;
    nextTokenId++;
    reservedMinted++;

    _safeMint(to, tokenId);
    _setTokenURI(tokenId, uri);
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/token/common/ERC2981.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/Pausable.sol";
import "@openzeppelin/contracts/utils/ReentrancyGuard.sol";

contract AdvancedNFT is ERC721URIStorage, ERC2981, Ownable, Pausable, ReentrancyGuard {
    uint256 public nextTokenId;
    uint256 public mintPrice = 0.015 ether;
    uint256 public maxSupply = 777;

    bool public revealed = false;
    string public hiddenURI;
    string public baseTokenURI;

    mapping(address => bool) public allowlist;
    bool public allowlistOnly = true;

    constructor() ERC721("Advanced NFT", "ADVNFT") Ownable(msg.sender) {
        _setDefaultRoyalty(msg.sender, 500); // 5%
    }

    function mint(string memory uri) external payable whenNotPaused nonReentrant {
        require(nextTokenId < maxSupply, "Max supply reached");
        require(msg.value >= mintPrice, "Insufficient payment");
        if (allowlistOnly) {
            require(allowlist[msg.sender], "Not allowlisted");
        }

        uint256 tokenId = nextTokenId++;
        _safeMint(msg.sender, tokenId);

        if (revealed) {
            _setTokenURI(tokenId, uri);
        }
    }

    function setAllowlist(address user, bool status) external onlyOwner {
        allowlist[user] = status;
    }

    function setAllowlistOnly(bool status) external onlyOwner {
        allowlistOnly = status;
    }

    function setHiddenURI(string memory _hiddenURI) external onlyOwner {
        hiddenURI = _hiddenURI;
    }

    function reveal(string memory _baseTokenURI) external onlyOwner {
        revealed = true;
        baseTokenURI = _baseTokenURI;
    }

    function tokenURI(uint256 tokenId) public view override returns (string memory) {
        _requireOwned(tokenId);
        if (!revealed) {
            return hiddenURI;
        }
        return super.tokenURI(tokenId);
    }

    function supportsInterface(bytes4 interfaceId)
        public
        view
        override(ERC721URIStorage, ERC2981)
        returns (bool)
    {
        return super.supportsInterface(interfaceId);
    }

    function withdraw() external onlyOwner nonReentrant {
        (bool success, ) = payable(owner()).call{value: address(this).balance}("");
        require(success, "Withdraw failed");
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/ReentrancyGuard.sol";

contract GovernanceNFT is ERC721URIStorage, Ownable, ReentrancyGuard {
    uint256 public nextTokenId;
    uint256 public maxSupply = 1000;
    uint256 public mintPrice = 0.05 ether;

    mapping(uint256 => uint256) public votingPower;
    mapping(address => uint256) public totalVotingPower;

    constructor() ERC721("Governance NFT", "GOVNFT") Ownable(msg.sender) {}

    function mint(string memory uri) external payable nonReentrant {
        require(nextTokenId < maxSupply, "Max supply reached");
        require(msg.value >= mintPrice, "Insufficient payment");

        uint256 tokenId = nextTokenId++;
        uint256 power = 1; // base power

        votingPower[tokenId] = power;
        totalVotingPower[msg.sender] += power;

        _safeMint(msg.sender, tokenId);
        _setTokenURI(tokenId, uri);
    }

    function _update(address to, uint256 tokenId, address auth)
        internal
        override
        returns (address)
    {
        address from = _ownerOf(tokenId);

        if (from != address(0)) {
            totalVotingPower[from] -= votingPower[tokenId];
        }
        if (to != address(0)) {
            totalVotingPower[to] += votingPower[tokenId];
        }

        return super._update(to, tokenId, auth);
    }

    function getVotingPower(address user) external view returns (uint256) {
        return totalVotingPower[user];
    }

    function increasePower(uint256 tokenId, uint256 amount) external onlyOwner {
        address owner_ = ownerOf(tokenId);
        votingPower[tokenId] += amount;
        totalVotingPower[owner_] += amount;
    }

    function withdraw() external onlyOwner {
        payable(owner()).transfer(address(this).balance);
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/ReentrancyGuard.sol";

contract FragmentNFT is ERC721URIStorage, Ownable, ReentrancyGuard {
    uint256 public nextTokenId;
    uint256 public maxSupply = 200;
    uint256 public mintPrice = 0.03 ether;
    uint256 public fragmentsNeeded = 5;

    mapping(address => uint256) public fragments;
    mapping(uint256 => bool) public isFragmented;

    constructor() ERC721("Fragment NFT", "FRAG") Ownable(msg.sender) {}

    function mint(string memory uri) external payable nonReentrant {
        require(nextTokenId < maxSupply, "Max supply reached");
        require(msg.value >= mintPrice, "Insufficient payment");

        uint256 tokenId = nextTokenId++;
        _safeMint(msg.sender, tokenId);
        _setTokenURI(tokenId, uri);
    }

    function fragment(uint256 tokenId) external {
        require(ownerOf(tokenId) == msg.sender, "Not owner");
        require(!isFragmented[tokenId], "Already fragmented");

        isFragmented[tokenId] = true;
        _burn(tokenId);
        fragments[msg.sender] += 1;
    }

    function redeem(string memory uri) external nonReentrant {
        require(fragments[msg.sender] >= fragmentsNeeded, "Not enough fragments");

        fragments[msg.sender] -= fragmentsNeeded;

        uint256 tokenId = nextTokenId++;
        _safeMint(msg.sender, tokenId);
        _setTokenURI(tokenId, uri);
    }

    function getFragments(address user) external view returns (uint256) {
        return fragments[user];
    }

    function withdraw() external onlyOwner {
        payable(owner()).transfer(address(this).balance);
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/Base64.sol";
import "@openzeppelin/contracts/utils/Strings.sol";

contract OnChainSVGNFT is ERC721, Ownable {
    using Strings for uint256;

    uint256 public nextTokenId;
    uint256 public maxSupply = 100;
    uint256 public mintPrice = 0.01 ether;

    mapping(uint256 => uint256) public tokenSeed;

    constructor() ERC721("OnChain SVG NFT", "SVGNFT") Ownable(msg.sender) {}

    function mint() external payable {
        require(nextTokenId < maxSupply, "Max supply reached");
        require(msg.value >= mintPrice, "Insufficient payment");

        uint256 tokenId = nextTokenId++;
        tokenSeed[tokenId] = uint256(keccak256(abi.encodePacked(block.timestamp, msg.sender, tokenId)));

        _safeMint(msg.sender, tokenId);
    }

    function tokenURI(uint256 tokenId) public view override returns (string memory) {
        _requireOwned(tokenId);

        uint256 seed = tokenSeed[tokenId];
        string memory color = _getColor(seed);
        string memory svg = string(abi.encodePacked(
            '<svg xmlns="http://www.w3.org/2000/svg" width="400" height="400">',
            '<rect width="400" height="400" fill="', color, '"/>',
            '<text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="white" font-size="24">',
            'Token #', tokenId.toString(),
            '</text></svg>'
        ));

        string memory json = Base64.encode(bytes(string(abi.encodePacked(
            '{"name":"SVG NFT #', tokenId.toString(),
            '","description":"Fully on-chain SVG NFT",',
            '"image":"data:image/svg+xml;base64,', Base64.encode(bytes(svg)), '"}'
        ))));

        return string(abi.encodePacked("data:application/json;base64,", json));
    }

    function _getColor(uint256 seed) internal pure returns (string memory) {
        string[6] memory colors = ["#FF6B6B", "#4ECDC4", "#45B7D1", "#96CEB4", "#FFEAA7", "#DDA0DD"];
        return colors[seed % 6];
    }

    function withdraw() external onlyOwner {
        payable(owner()).transfer(address(this).balance);
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/ReentrancyGuard.sol";

contract CollaborativeNFT is ERC721URIStorage, Ownable, ReentrancyGuard {
    uint256 public nextTokenId;
    uint256 public maxSupply = 50;
    uint256 public mintPrice = 0.1 ether;

    mapping(uint256 => address[]) public coOwners;
    mapping(uint256 => mapping(address => bool)) public isCoOwner;
    mapping(uint256 => uint256) public approvalCount;
    mapping(uint256 => mapping(address => bool)) public hasApproved;

    constructor() ERC721("Collaborative NFT", "COOP") Ownable(msg.sender) {}

    function mint(string memory uri, address[] memory initialCoOwners) external payable nonReentrant {
        require(nextTokenId < maxSupply, "Max supply reached");
        require(msg.value >= mintPrice, "Insufficient payment");
        require(initialCoOwners.length >= 2, "Need at least 2 co-owners");

        uint256 tokenId = nextTokenId++;
        _safeMint(msg.sender, tokenId);
        _setTokenURI(tokenId, uri);

        for (uint256 i = 0; i < initialCoOwners.length; i++) {
            address coOwner = initialCoOwners[i];
            coOwners[tokenId].push(coOwner);
            isCoOwner[tokenId][coOwner] = true;
        }
    }

    function proposeTransfer(uint256 tokenId) external {
        require(isCoOwner[tokenId][msg.sender], "Not a co-owner");
        require(!hasApproved[tokenId][msg.sender], "Already approved");

        hasApproved[tokenId][msg.sender] = true;
        approvalCount[tokenId]++;
    }

    function executeTransfer(uint256 tokenId, address to) external nonReentrant {
        require(isCoOwner[tokenId][msg.sender], "Not a co-owner");
        require(approvalCount[tokenId] >= coOwners[tokenId].length, "Not enough approvals");

        // Reset approvals
        for (uint256 i = 0; i < coOwners[tokenId].length; i++) {
            hasApproved[tokenId][coOwners[tokenId][i]] = false;
        }
        approvalCount[tokenId] = 0;

        _transfer(ownerOf(tokenId), to, tokenId);
    }

    function getCoOwners(uint256 tokenId) external view returns (address[] memory) {
        return coOwners[tokenId];
    }

    function withdraw() external onlyOwner {
        payable(owner()).transfer(address(this).balance);
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract GuildTreasury {
    address public owner;
    mapping(address => bool) public isMember;
    uint256 public memberCount;

    event Deposited(address indexed from, uint256 amount);
    event Withdrawn(address indexed to, uint256 amount);
    event MemberAdded(address indexed member);
    event MemberRemoved(address indexed member);

    modifier onlyOwner() {
        require(msg.sender == owner, "Not owner");
        _;
    }

    modifier onlyMember() {
        require(isMember[msg.sender], "Not a member");
        _;
    }

    constructor(address[] memory initialMembers) {
        owner = msg.sender;
        for (uint i = 0; i < initialMembers.length; i++) {
            isMember[initialMembers[i]] = true;
            memberCount++;
            emit MemberAdded(initialMembers[i]);
        }
    }

    receive() external payable {
        emit Deposited(msg.sender, msg.value);
    }

    function addMember(address member) external onlyOwner {
        require(!isMember[member], "Already member");
        isMember[member] = true;
        memberCount++;
        emit MemberAdded(member);
    }

    function removeMember(address member) external onlyOwner {
        require(isMember[member], "Not a member");
        isMember[member] = false;
        memberCount--;
        emit MemberRemoved(member);
    }

    function withdraw(uint256 amount, address payable to) external onlyMember {
        require(address(this).balance >= amount, "Insufficient balance");
        (bool success, ) = to.call{value: amount}("");
        require(success, "Transfer failed");
        emit Withdrawn(to, amount);
    }

    function getBalance() external view returns (uint256) {
        return address(this).balance;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

contract GuildMarketplace is ReentrancyGuard {
    struct Listing {
        address seller;
        address nftContract;
        uint256 tokenId;
        uint256 price;
        bool active;
    }

    mapping(uint256 => Listing) public listings;
    uint256 public listingCount;
    uint256 public feePercent = 250; // 2.5%
    address public feeReceiver;

    event Listed(uint256 indexed listingId, address seller, address nft, uint256 tokenId, uint256 price);
    event Sold(uint256 indexed listingId, address buyer, uint256 price);
    event Cancelled(uint256 indexed listingId);

    constructor(address _feeReceiver) {
        feeReceiver = _feeReceiver;
    }

    function listNFT(address nftContract, uint256 tokenId, uint256 price) external {
        require(price > 0, "Price must be > 0");
        IERC721(nftContract).transferFrom(msg.sender, address(this), tokenId);

        uint256 id = listingCount++;
        listings[id] = Listing(msg.sender, nftContract, tokenId, price, true);

        emit Listed(id, msg.sender, nftContract, tokenId, price);
    }

    function buyNFT(uint256 listingId) external payable nonReentrant {
        Listing storage listing = listings[listingId];
        require(listing.active, "Not active");
        require(msg.value >= listing.price, "Insufficient payment");

        listing.active = false;

        uint256 fee = (listing.price * feePercent) / 10000;
        uint256 sellerAmount = listing.price - fee;

        (bool success1, ) = listing.seller.call{value: sellerAmount}("");
        require(success1, "Seller transfer failed");
        (bool success2, ) = feeReceiver.call{value: fee}("");
        require(success2, "Fee transfer failed");

        // Refund excess
        if (msg.value > listing.price) {
            (bool success3, ) = msg.sender.call{value: msg.value - listing.price}("");
            require(success3, "Refund failed");
        }

        IERC721(listing.nftContract).transferFrom(address(this), msg.sender, listing.tokenId);
        emit Sold(listingId, msg.sender, listing.price);
    }

    function cancelListing(uint256 listingId) external {
        Listing storage listing = listings[listingId];
        require(listing.seller == msg.sender, "Not seller");
        require(listing.active, "Not active");

        listing.active = false;
        IERC721(listing.nftContract).transferFrom(address(this), msg.sender, listing.tokenId);
        emit Cancelled(listingId);
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract GuildRaffle {
    address public owner;
    uint256 public ticketPrice;
    uint256 public maxTickets;
    address[] public players;
    bool public isActive;
    address public winner;

    event TicketBought(address indexed player, uint256 ticketNumber);
    event WinnerSelected(address indexed winner, uint256 prize);

    modifier onlyOwner() {
        require(msg.sender == owner, "Not owner");
        _;
    }

    constructor(uint256 _ticketPrice, uint256 _maxTickets) {
        owner = msg.sender;
        ticketPrice = _ticketPrice;
        maxTickets = _maxTickets;
        isActive = true;
    }

    function buyTicket() external payable {
        require(isActive, "Raffle closed");
        require(msg.value == ticketPrice, "Incorrect value");
        require(players.length < maxTickets, "Sold out");

        players.push(msg.sender);
        emit TicketBought(msg.sender, players.length);
    }

    function drawWinner() external onlyOwner {
        require(isActive, "Already drawn");
        require(players.length > 0, "No players");

        isActive = false;
        uint256 randomIndex = uint256(keccak256(abi.encodePacked(block.timestamp, block.prevrandao, players.length))) % players.length;
        winner = players[randomIndex];

        uint256 prize = address(this).balance;
        (bool success, ) = winner.call{value: prize}("");
        require(success, "Transfer failed");

        emit WinnerSelected(winner, prize);
    }

    function getPlayers() external view returns (address[] memory) {
        return players;
    }

    function getPlayerCount() external view returns (uint256) {
        return players.length;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract GuildPaymentSplitter {
    address[] public payees;
    mapping(address => uint256) public shares;
    mapping(address => uint256) public released;
    uint256 public totalShares;
    uint256 public totalReleased;

    event PayeeAdded(address account, uint256 shares);
    event PaymentReleased(address to, uint256 amount);
    event PaymentReceived(address from, uint256 amount);

    constructor(address[] memory _payees, uint256[] memory _shares) {
        require(_payees.length == _shares.length, "Length mismatch");
        require(_payees.length > 0, "No payees");

        for (uint256 i = 0; i < _payees.length; i++) {
            _addPayee(_payees[i], _shares[i]);
        }
    }

    receive() external payable {
        emit PaymentReceived(msg.sender, msg.value);
    }

    function release(address account) public {
        require(shares[account] > 0, "No shares");
        uint256 totalReceived = address(this).balance + totalReleased;
        uint256 payment = (totalReceived * shares[account]) / totalShares - released[account];
        require(payment > 0, "No payment due");

        released[account] += payment;
        totalReleased += payment;
        (bool success, ) = account.call{value: payment}("");
        require(success, "Transfer failed");
        emit PaymentReleased(account, payment);
    }

    function releaseAll() external {
        for (uint256 i = 0; i < payees.length; i++) {
            release(payees[i]);
        }
    }

    function _addPayee(address account, uint256 share) private {
        require(account != address(0), "Invalid address");
        require(share > 0, "Shares must be > 0");
        require(shares[account] == 0, "Already has shares");

        payees.push(account);
        shares[account] = share;
        totalShares += share;
        emit PayeeAdded(account, share);
    }

    function getPayees() external view returns (address[] memory) {
        return payees;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract GuildTipJar {
    address public owner;
    address public beneficiary;
    uint256 public goal;
    uint256 public totalRaised;
    bool public goalReached;

    mapping(address => uint256) public contributions;

    event Tipped(address indexed from, uint256 amount);
    event GoalReached(uint256 total);
    event Withdrawn(uint256 amount);

    modifier onlyOwner() {
        require(msg.sender == owner, "Not owner");
        _;
    }

    constructor(address _beneficiary, uint256 _goal) {
        owner = msg.sender;
        beneficiary = _beneficiary;
        goal = _goal;
    }

    function tip() external payable {
        require(msg.value > 0, "Must send ETH");
        require(!goalReached, "Goal already reached");

        contributions[msg.sender] += msg.value;
        totalRaised += msg.value;

        emit Tipped(msg.sender, msg.value);

        if (totalRaised >= goal) {
            goalReached = true;
            emit GoalReached(totalRaised);
        }
    }

    function withdraw() external onlyOwner {
        require(goalReached, "Goal not reached yet");
        uint256 amount = address(this).balance;
        (bool success, ) = beneficiary.call{value: amount}("");
        require(success, "Transfer failed");
        emit Withdrawn(amount);
    }

    function changeBeneficiary(address newBeneficiary) external onlyOwner {
        beneficiary = newBeneficiary;
    }

    function getProgress() external view returns (uint256 raised, uint256 target, bool reached) {
        return (totalRaised, goal, goalReached);
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract GuildCheckIn {
    address public owner;
    uint256 public eventId;
    
    struct Event {
        string name;
        uint256 startTime;
        uint256 endTime;
        bool active;
        mapping(address => bool) attended;
        uint256 attendeeCount;
    }

    mapping(uint256 => Event) public events;

    event EventCreated(uint256 indexed id, string name, uint256 start, uint256 end);
    event CheckedIn(uint256 indexed eventId, address indexed user);

    modifier onlyOwner() {
        require(msg.sender == owner, "Not owner");
        _;
    }

    constructor() {
        owner = msg.sender;
    }

    function createEvent(string calldata name, uint256 startTime, uint256 endTime) external onlyOwner returns (uint256) {
        require(endTime > startTime, "Invalid time");
        uint256 id = eventId++;
        Event storage e = events[id];
        e.name = name;
        e.startTime = startTime;
        e.endTime = endTime;
        e.active = true;

        emit EventCreated(id, name, startTime, endTime);
        return id;
    }

    function checkIn(uint256 id) external {
        Event storage e = events[id];
        require(e.active, "Event not active");
        require(block.timestamp >= e.startTime && block.timestamp <= e.endTime, "Not in time window");
        require(!e.attended[msg.sender], "Already checked in");

        e.attended[msg.sender] = true;
        e.attendeeCount++;
        emit CheckedIn(id, msg.sender);
    }

    function hasAttended(uint256 id, address user) external view returns (bool) {
        return events[id].attended[user];
    }

    function closeEvent(uint256 id) external onlyOwner {
        events[id].active = false;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

contract GuildTokenLocker {
    using SafeERC20 for IERC20;

    struct Lock {
        address token;
        uint256 amount;
        uint256 unlockTime;
        bool withdrawn;
    }

    mapping(address => Lock[]) public locks;

    event Locked(address indexed user, address token, uint256 amount, uint256 unlockTime, uint256 lockId);
    event Withdrawn(address indexed user, uint256 lockId, uint256 amount);

    function lockTokens(address token, uint256 amount, uint256 lockDuration) external {
        require(amount > 0, "Amount must be > 0");
        require(lockDuration > 0, "Duration must be > 0");

        IERC20(token).safeTransferFrom(msg.sender, address(this), amount);

        uint256 unlockTime = block.timestamp + lockDuration;
        locks[msg.sender].push(Lock({
            token: token,
            amount: amount,
            unlockTime: unlockTime,
            withdrawn: false
        }));

        uint256 lockId = locks[msg.sender].length - 1;
        emit Locked(msg.sender, token, amount, unlockTime, lockId);
    }

    function withdraw(uint256 lockId) external {
        require(lockId < locks[msg.sender].length, "Invalid lockId");
        Lock storage userLock = locks[msg.sender][lockId];
        require(!userLock.withdrawn, "Already withdrawn");
        require(block.timestamp >= userLock.unlockTime, "Still locked");

        userLock.withdrawn = true;
        IERC20(userLock.token).safeTransfer(msg.sender, userLock.amount);
        emit Withdrawn(msg.sender, lockId, userLock.amount);
    }

    function getLocks(address user) external view returns (Lock[] memory) {
        return locks[user];
    }

    function getLockCount(address user) external view returns (uint256) {
        return locks[user].length;
    }
}
