// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleVoting {
    address public owner;
    bool public electionStarted;
    bool public electionEnded;

    struct Candidate {
        uint id;
        string name;
        uint voteCount;
    }

    struct Voter {
        bool hasVoted;
        uint vote;
    }

    mapping(address => Voter) public voters;
    mapping(uint => Candidate) public candidates;

    uint public candidatesCount;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can perform this action");
        _;
    }

    function addCandidate(string memory _name) public onlyOwner {
        require(!electionStarted, "Cannot add candidates after election starts");
        candidatesCount++;
        candidates[candidatesCount] = Candidate(candidatesCount, _name, 0);
    }

    function startElection() public onlyOwner {
        require(!electionStarted, "Election already started");
        electionStarted = true;
        electionEnded = false;
    }

    function vote(uint _candidateId) public {
        require(electionStarted, "Election not started yet");
        require(!electionEnded, "Election already ended");
        require(!voters[msg.sender].hasVoted, "You have already voted");
        require(_candidateId > 0 && _candidateId <= candidatesCount, "Invalid candidate");

        voters[msg.sender].hasVoted = true;
        voters[msg.sender].vote = _candidateId;

        candidates[_candidateId].voteCount++;
    }

    function endElection() public onlyOwner {
        require(electionStarted, "Election not started yet");
        electionEnded = true;
        electionStarted = false;
    }

    function getWinner() public view returns (string memory winnerName, uint winnerVotes) {
        require(electionEnded, "Election has not ended yet");

        uint maxVotes = 0;
        uint winnerId = 0;

        for (uint i = 1; i <= candidatesCount; i++) {
            if (candidates[i].voteCount > maxVotes) {
                maxVotes = candidates[i].voteCount;
                winnerId = i;
            }
        }

        winnerName = candidates[winnerId].name;
        winnerVotes = candidates[winnerId].voteCount;
    }
}
