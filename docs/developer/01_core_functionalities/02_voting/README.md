# Voting
   - **Purpose**: Allow users to upvote or downvote submissions to signal quality and trustworthiness.
   - **Implementation Details**:
     - **Technology**: Ethereum smart contract for voting logic, blockchain event listeners for real-time voting updates, and Web3.js (or Ethers.js) integration for plugin interactions.
     - **Voting API**: Implement a `POST /vote` API on the backend instance that interacts with the smart contract.
     - **Frontend Integration**: Update submission scores dynamically in the browser plugin via WebSockets or a polling mechanism to ensure real-time feedback.
     - **Smart Contract Logic**: Set up functions to adjust karma based on upvotes/downvotes. Ensure karma deduction for voting to prevent spam.