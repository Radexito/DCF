# Decentralized Content Filter - Backend Instance Developer README

## Table of Contents
1. [Overview](#overview)
2. [Backend Server Requirements](#backend-server-requirements)
3. [API Endpoints](#api-endpoints)
   - [User Submission Endpoint](#user-submission-endpoint)
   - [Voting Endpoint](#voting-endpoint)
   - [Karma Management Endpoint](#karma-management-endpoint)
   - [Uberscript Management Endpoint](#uberscript-management-endpoint)
4. [Database Structure](#database-structure)
5. [Blockchain Integration](#blockchain-integration)
6. [Security and Access Control](#security-and-access-control)
7. [Deployment](#deployment)
8. [Testing and Maintenance](#testing-and-maintenance)

---

## Overview
The backend instance serves as a bridge between the browser plugin and the smart contract, handling content filtering submissions, vote management, and syncing with the blockchain. Instances can be self-hosted or configured on platforms like AWS, and they store data locally to enhance performance and ensure efficient syncing with the smart contract.

### Technology Stack
- **Server**: Flask or Express.js
- **Database**: PostgreSQL or MongoDB
- **Blockchain Library**: Web3.js or Ethers.js for blockchain interactions

---

## Backend Server Requirements

1. **Public Port Access**: For network contributions, each instance must open a public port to provide data access to other backend instances and the browser plugin.
2. **Blockchain Sync**: Instances periodically sync with the smart contract to update karma, votes, and registered instances.
3. **API Security**: Each endpoint requires token-based or IP-restricted access to secure user submissions and voting actions.

---

## API Endpoints

### User Submission Endpoint
   - **Endpoint**: `POST /submit`
   - **Purpose**: Accepts user submissions of flagged content, including usernames, links, or other content identifiers.
   - **Parameters**: 
     - `username`: The flagged account username (optional).
     - `content_link`: Link to the flagged content.
     - `content_type`: Type of content (e.g., post, comment).
     - `reason`: Textual reason for flagging.
   - **Response**: `200 OK` with `submissionId`.
   - **Blockchain Sync**: Stores submission data locally and periodically syncs with the smart contract to ensure blockchain record consistency.

### Voting Endpoint
   - **Endpoint**: `POST /vote`
   - **Purpose**: Allows users to vote on flagged submissions, influencing visibility and content trust levels.
   - **Parameters**: 
     - `submissionId`: ID of the flagged submission.
     - `voteType`: Boolean (`true` for upvote, `false` for downvote).
   - **Response**: `200 OK` with updated vote count.
   - **Logic**: Adjusts karma and deducts points from the user’s balance for each vote to ensure fair voting. Syncs vote data with the smart contract to maintain consistency.

### Karma Management Endpoint
   - **Endpoint**: `POST /updateKarma`
   - **Purpose**: Adjusts karma based on actions (e.g., submissions, voting).
   - **Parameters**:
     - `userAddress`: User’s blockchain address.
     - `karmaChange`: Integer change in karma (positive or negative).
   - **Response**: `200 OK` with updated karma balance.
   - **Notes**: Only callable by authorized instances or the smart contract.

### Uberscript Management Endpoint
   - **Endpoint**: `GET /uberscripts` and `POST /voteUberscript`
   - **Purpose**: Fetches available uberscripts and enables voting on uberscripts for community approval.
   - **Parameters**:
     - For `GET /uberscripts`: None.
     - For `POST /voteUberscript`: `uberscriptId` and `voteType`.
   - **Response**:
     - `GET /uberscripts`: JSON list of uberscripts.
     - `POST /voteUberscript`: Updated vote count for the selected uberscript.
   - **Logic**: Fetches and stores uberscript data locally, syncing with the smart contract for approval tracking and vote tallies.

---

## Database Structure

1. **Tables/Collections**:
   - `submissions`: Stores flagged content data, including submission IDs, content links, types, and reasons.
   - `votes`: Tracks votes cast on submissions, linking to submission IDs and user addresses.
   - `karma`: Stores user karma balances and logs changes over time.
   - `uberscripts`: Holds uberscript data, including script IDs, vote counts, and approval status.

2. **Relationships**:
   - **One-to-Many**: Each user can have multiple submissions and votes.
   - **Foreign Keys/References**: `submissionId` in `votes` table refers to the primary key in `submissions`.

3. **Indexing**:
   - Index frequently queried fields like `submissionId`, `userAddress`, and `uberscriptId` to improve performance.

---

## Blockchain Integration

1. **Web3.js or Ethers.js**: Use these libraries to interact with the Ethereum or Polygon network.
2. **Smart Contract Calls**:
   - **registerInstance**: Called when a new instance is deployed to ensure it’s recognized by the smart contract.
   - **updateKarma**: Syncs local karma changes with the blockchain.
   - **voteOnSubmission** and **voteOnUberscript**: Records votes and updates respective counts on-chain.
3. **Event Listeners**: Use blockchain event listeners to track and confirm on-chain events like instance registrations, vote confirmations, and karma updates.

---

## Security and Access Control

1. **Token-Based Authentication**: Secure API endpoints with token-based authentication (e.g., JWT) to ensure only authorized requests access sensitive functions.
2. **IP Whitelisting**: Optionally limit access to known IP ranges for added security.
3. **Data Validation**: Sanitize and validate all incoming data to protect against injection attacks.
4. **Rate Limiting**: Apply rate limiting on endpoints, especially voting, to prevent abuse and spam.

---

## Deployment

1. **Environment Setup**:
   - Set environment variables for database credentials, blockchain keys, and API keys.
   - Configure public port access to ensure the instance is reachable for data sharing and contribution.

2. **Database Configuration**:
   - Initialize and configure PostgreSQL or MongoDB.
   - Set up database schema with migrations or schema definitions as needed.

3. **Deployment Options**:
   - **Self-Hosting**: Recommended for local or private use.
   - **AWS S3 or EC2**: Use a scalable cloud service with pre-configured instance images for simplified deployment.

4. **Syncing**:
   - Schedule regular blockchain syncing (e.g., hourly or daily) to ensure local data aligns with the smart contract’s state.

---

## Testing and Maintenance

### Testing
1. **Unit Testing**: Test each API endpoint for expected responses, data handling, and security validations.
2. **Integration Testing**: Test end-to-end flows including user submissions, voting, and blockchain sync.
3. **Load Testing**: Ensure server handles high-traffic situations effectively, especially for public-facing instances.

### Maintenance
1. **Periodic Blockchain Sync**: Ensure backend data remains consistent with the blockchain state.
2. **Database Optimization**: Monitor query performance and optimize indexing periodically.
3. **Monitoring**: Use monitoring tools to track API performance, errors, and uptime.
4. **Backup**: Implement regular backups for database and configuration settings to prevent data loss.

---

This developer README provides a structured overview of backend setup, including API endpoint specifications, security practices, and deployment guidelines. Follow these instructions to set up, deploy, and maintain a backend instance that integrates with the Decentralized Content Filter network.
