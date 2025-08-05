# 💰 Metal CordApp

A simple Corda CorDapp for issuing and transferring a digital asset called **Metal** (e.g., Gold) between parties. This project demonstrates smart contract enforcement, custom flows, and vault queries using the Corda blockchain platform.

---

## 🧾 Description

This CorDapp simulates real-world asset management for digital metals by enabling the following:

- ✅ Issuance of a metal asset by a minting party to a trader  
- 🔁 Transfer of ownership between traders  
- 🔍 Vault search to view all stored metal states  

It is intended as a learning project to understand how to build decentralized applications with **Corda**, covering contracts, states, flows, and vault services.

---



---

## ⚙️ Setup

### 1. Build and Deploy Nodes

Run the following command to build the project and generate the node directories:

```bash
./gradlew clean deployNodes
```
### Start the Nodes
```
build/nodes/runnodes.bat
```
##  Running Flows
###  Issue Flows (Run in Mint Node Terminal)

#### Issue to Trader A
```
start IssueMetal metalName: Gold, weight: 10, owner: "O=TraderA,L=New York,C=US"
```
#### Issue to Trader B
```
start IssueMetal metalName: Gold, weight: 20, owner: "O=Traderb,L=New York,C=US"
```
### 🔁 Transfer Flow (Run in Trader A Node Terminal)
```
start TransferMetal metalName: Gold, weight: 10, newOwner: "O=TraderB,L=New York,C=US"
```
### 🔍 Search Vault (Run in Trader B Node Terminal)
```
run vaultQuery contractStateType: com.template.states.MetalState
```
📜 Contract Rules
Issue Command
Must have 0 inputs

Must have 1 output of type MetalState

Metal name must be "Gold" (case-sensitive)

Issuer must be a required signer

Transfer Command
Must have 1 input and 1 output

Input and output must both be MetalState

Metal must be "Gold"

Previous owner must be a required signer

## 🧪 Testing
You can test the contract rules by running the JUnit tests in ContractTests.java. These cover:

- Zero inputs in issue command
- One output in issue command
- Correct type of output
- Required signers
- Proper command types (issue, transfer)

## 📚 Prerequisites
- Java 11 or later
- IntelliJ IDEA with Corda plugin
- Corda open-source version




