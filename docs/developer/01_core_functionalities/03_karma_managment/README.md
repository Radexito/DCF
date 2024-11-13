# Karma Management
   - **Purpose**: Maintain a self-regulating karma economy to reward valuable contributions and limit spam.
   - **Implementation Details**:
     - **Technology**: Karma logic managed through the smart contract, integrating with instance databases for real-time karma calculations.
     - **Karma Accumulation**: Implement functions in the smart contract to increase karma based on verified, helpful submissions and successful upvotes.
     - **Karma Decay**: Set a periodic decay rate (e.g., monthly) to be managed by a backend cron job that updates each user’s karma balance, promoting continuous participation.
     - **Frontend**: Display karma in the browser plugin with an option for users to set visibility preferences.