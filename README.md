Experiment 1: Decentralized Certificate Verification
Name:prabanjan.m
reg no: 212224240116
Aim: 
To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.

Algorithm:
Deploy a smart contract where universities can issue certificates.
Store a hash of certificate data on-chain.
Provide a verification function that checks certificate authenticity.
Users can verify the certificate by comparing the stored hash.
Program:
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
Output:
<img width="1920" height="1140" alt="Screenshot 2026-02-25 092045" src="https://github.com/user-attachments/assets/fb6b5730-93fe-4361-bf41-e8f88b8cf1df" />

Expected Output:
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
Result:
Thus the smart contract for issuing and verifying academic certificates on Ethereum is successfully deployed.
