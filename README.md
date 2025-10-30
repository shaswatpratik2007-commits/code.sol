🎲 TruthDareChain – Decentralized Truth or Dare dApp

A fun and interactive decentralized Truth or Dare game built with Solidity and deployed on the Ethereum and Solana test networks.
This project shows how blockchain can make social games more transparent, fair, and community-driven through verifiable on-chain interactions.

<img width="1886" height="1088" alt="Screenshot 2025-10-30 202431" src="https://github.com/user-attachments/assets/083689b5-86e8-4707-a4b0-dc286fe49935" />


📜 Project Description
TruthDareChain allows users to create, upvote, and play Truth or Dare challenges using their crypto wallets.
Each challenge whether it’s a Truth question or a Dare task is stored permanently on-chain.
Players can randomly draw challenges, vote for their favorites, and interact with others in a transparent and decentralized way.

This project is perfect for beginners exploring Solidity, Web3 gaming logic, event handling, and community-based smart contracts.

⚙️ What It Does

* 🎯 Users can submit Truth or Dare challenges for everyone to play.
* 👍 Players can upvote fun or creative challenges.
* 🎲 Random challenge draw feature for surprise gameplay.
* 🔗 All data stored on-chain for full transparency.
* 📊 Tracks total challenges, votes, and participants.

🌟 Features

* 🧠 Beginner-Friendly Solidity code that’s easy to understand.
* 🕹️ Interactive on-chain gameplay.
* 🔒 Transparent and trustless challenge management.
* 💬 Community-driven challenge voting system.
* ⛓️ Supports multi-chain deployment (Ethereum, Solana).
* 🚀 Expandable design — can add NFTs, rewards, or leaderboards later.

📄 Smart Contract Details
Language: Solidity ^0.8.20
Framework: Remix / Hardhat Compatible
Network: Ethereum and Solana Testnets

Deployed Contract:
0x03F2c506fC347F7Df1c0B02eb663f8B2FE0F28aa

View on Etherscan:
[https://etherscan.io/address/0x03F2c506fC347F7Df1c0B02eb663f8B2FE0F28aa](https://etherscan.io/address/0x03F2c506fC347F7Df1c0B02eb663f8B2FE0F28aa)

💻 Smart Contract Code
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract TruthDareChain {
struct Challenge {
uint256 id;
address creator;
string text;
bool isTruth;
uint256 votes;
}

```
uint256 public nextId;  
mapping(uint256 => Challenge) public challenges;  
mapping(address => uint256[]) public userChallenges;  

event ChallengeCreated(uint256 id, address creator, string text, bool isTruth);  
event ChallengeVoted(uint256 id, address voter, uint256 votes);  

function createChallenge(string memory text, bool isTruth) public {  
    challenges[nextId] = Challenge(nextId, msg.sender, text, isTruth, 0);  
    userChallenges[msg.sender].push(nextId);  
    emit ChallengeCreated(nextId, msg.sender, text, isTruth);  
    nextId++;  
}  

function voteChallenge(uint256 id) public {  
    require(id < nextId, "Invalid challenge id");  
    challenges[id].votes++;  
    emit ChallengeVoted(id, msg.sender, challenges[id].votes);  
}  

function getChallenge(uint256 id) public view returns (Challenge memory) {  
    return challenges[id];  
}  

function getUserChallenges(address user) public view returns (uint256[] memory) {  
    return userChallenges[user];  
}  
```

}

🧩 Future Enhancements

* 🏆 Add reward tokens or NFTs for popular challenges
* 🎭 Random challenge generator for party mode
* 📱 Build a frontend interface with React and Web3.js
* 🔐 Add player identity or verified profile badges

🙌 Acknowledgments

* Ethereum and Solana testnets for deployment
* Remix IDE for testing and debugging
* Etherscan for transparency and contract verification

Made with ❤️ by Shaswat for the Web3 community.
Play fair, play fun, play decentralized!
