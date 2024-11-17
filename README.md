# Simple Subscription Service - Smart Contract

## Overview  
The **Simple Subscription Service** is a Solidity smart contract designed to handle subscription-based payments on the Ethereum blockchain. It allows customers to start subscriptions, cancel them, or request refunds. The contract owner can also manage subscriptions efficiently, ensuring a seamless and transparent subscription model.

---

## Features  
### Core Functionalities  
- **Start a Subscription**: Customers can start a subscription by paying a minimum amount of Ether.  
- **Cancel a Subscription**: Active subscribers can cancel their subscriptions at any time if their subscription is not delivered.  
- **Refund Management**: The owner can refund inactive subscriptions, ensuring accountability.  
- **Active Subscription Monitoring**: Check the total number of active subscriptions at any time.

### Administrative Features  
- **Owner Access**: Only the contract owner can perform certain actions, like processing refunds.  
- **Secure Fund Management**: The contract securely handles Ether transactions and maintains accurate tracking of funds.

---

## Prerequisites  
- Ethereum wallet compatible with the Solidity version `0.8.27`.  
- **Test Environment**: Use platforms like [Remix](https://remix.ethereum.org/) or a local Ethereum testnet such as [Hardhat](https://hardhat.org/).  
- **Metamask** or any Web3 wallet for testing transactions.  

---

## Installation  
### Steps to Deploy  
1. **Clone the Repository**:  
   ```bash
   git clone https://github.com/your-repo/simple-subscription-service.git
   cd simple-subscription-service
   ```  

2. **Compile the Contract**:  
   - Open the `.sol` file in [Remix](https://remix.ethereum.org/).  
   - Select Solidity version `0.8.27`.  
   - Compile the `SimpleSubscriptionService` contract.  

3. **Deploy**:  
   - Choose a test network like **Rinkeby** or **Ganache**.  
   - Deploy the contract using your wallet.  

---

## Usage Instructions  
### Starting a Subscription  
- **Action**: Call the `startSubscription` function.  
- **Requirement**: Pay at least `0.01 ether`.  
- **Example**:  
  ```solidity
  startSubscription("Customer1", { value: 0.05 ether });
  ```
- **Result**: Subscription details are stored, and the subscription is active.  

---

### Cancelling a Subscription  
- **Action**: Call the `cancelSubscription` function.  
- **Requirement**: The subscription must be active and owned by the caller.  
- **Example**:  
  ```solidity
  cancelSubscription(1);
  ```
- **Result**: Subscription is cancelled, and funds are retained unless refunded.  

---

### Refunding a Subscription  
- **Action**: Call the `refundSubscription` function (owner only).  
- **Requirement**: The subscription must be inactive and must exist.  
- **Example**:  
  ```solidity
  refundSubscription(1);
  ```
- **Result**: Ether is refunded to the original subscriber, and subscription details are marked as refunded.  

---

### Viewing Active Subscriptions  
- **Action**: Call the `getActiveSubscriptionCount` function.  
- **Example**:  
  ```solidity
  getActiveSubscriptionCount();
  ```
- **Result**: Returns the number of currently active subscriptions.  

---

## Contract Details  
### State Variables  
- `owner`: Stores the address of the contract deployer.  
- `subscriptionCount`: Tracks the total number of subscriptions.  
- `subscriptions`: Mapping that holds all subscription details indexed by subscription ID.

### Structs  
- `Subscription`: Holds subscription information such as ID, subscriber address, payment details, and status.

---

## Error Handling  
### Require Statements  
- **Minimum Payment**: Subscription payments must meet the minimum threshold.  
- **Ownership Checks**: Only owners can refund subscriptions or perform administrative actions.  

### Revert Statements  
- **Refund Failures**: Refunds are reverted if a transfer fails.  

---

## Tests  
- **Test Cases**:  
  - Starting a subscription with `0.01 ether` (pass).  
  - Cancelling an active subscription by the subscriber (pass).  
  - Attempting to cancel another user's subscription (fail).  
  - Refunds initiated by the owner (pass).  

- **Test Environment**: Run tests on [Remix](https://remix.ethereum.org/) or integrate with [Hardhat](https://hardhat.org/).  

---

## Contributing  
1. Fork the repository.  
2. Create a new branch:  
   ```bash
   git checkout -b feature/your-feature
   ```  
3. Commit your changes:  
   ```bash
   git commit -m 'Add your feature'
   ```  
4. Push to the branch:  
   ```bash
   git push origin feature/your-feature
   ```  
5. Open a Pull Request.  

---

## License  
This project is licensed under the **MIT License**.  

---

## Author  
- **Your Name**  
- GitHub: https://github.com/whybecauseican

---  

## Acknowledgments  
- Ethereum development community.  
- Solidity official documentation.  
- Remix IDE for testing and debugging.
