# User Submissions
   - **Purpose**: Enable users to flag spammy/misleading content by submitting usernames, links, or specific posts for review.
   - **Implementation Details**:
     - **Technology**: JSON schema for defining submission format, REST API endpoints for submission handling, and smart contract calls to register submissions.
     - **API Structure**: Define `POST /submit` endpoint with fields for `username`, `content_link`, `content_type`, and `reason`. Ensure JSON data is sanitized and validated.
     - **Data Storage**: Store submissions on the backend instance, with periodic synchronization to the blockchain for trusted instances.
     - **Smart Contract**: Add functionality for recording submissions on-chain, maintaining immutability for registered submissions.
