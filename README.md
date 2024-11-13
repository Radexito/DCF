
# Decentralized Content Filter

## Introduction

Let’s fix the web by creating a global system to promote genuine content and demote spammy or misleading material. The Decentralized Content Filter is designed to operate across a wide range of platforms—Reddit, Facebook, YouTube, Netflix, blogs, and more. This open-source browser plugin allows users to filter or score content based on its quality or authenticity, according to community-driven standards. Users can choose to hide flagged content entirely or simply lower its visibility with a “respect score,” based on their preferences.

To ensure efficient operation, users are encouraged to host their own backend instance. Otherwise, they risk sending a high volume of requests from websites to a public backend, which could slow down the browsing experience. By running local instances, we promote decentralization and faster, more private filtering for all users.

## Project Overview

The Decentralized Content Filter project is a community-driven solution for identifying and filtering spam or misleading content across various platforms. It empowers users to control what they see online, using community-vetted filters and a decentralized infrastructure. This project also introduces a unique system for creating and using “uberscripts” that can override entire website UIs.

### Goals:

1.  User-Controlled Moderation: Give users the power to identify and filter misleading or spammy content.
    
2.  Decentralized Infrastructure: Enable users to connect to their own backend instances or community-vetted instances.
    
3.  Self-Sustaining Ecosystem: Operate on a karma-based voting and donation system to sustain the project.
    
4.  Anonymity and Privacy: Ensure that no personal information is collected from users.
    

## Architecture

The project consists of three main components:

1.  Browser Plugin (Frontend): A Chrome/Firefox extension that enables users to filter content, submit flagged content, and vote on flagged items.
    
2.  Backend Instances: Server packages that host filtering data and sync with the blockchain ledger to provide data for the browser plugin. Instances can be self-hosted or purchased as pre-configured instances on platforms like S3.
    
3.  Smart Contract (Blockchain): A smart contract that manages instance registration, karma-based voting, and the trusted instance list.
    

### Key Functionalities

1.  User Submissions: Users can submit usernames suspected of being spam accounts or links to flagged content, along with additional metadata provided in JSON format or possibly through a userscript or similar tool. This additional data helps categorize, review, and evaluate content accurately.
    
2.  Voting System: Users earn karma for valuable submissions and spend karma to vote on flagged content.
    
3.  Instance Registration: Instances are registered with the smart contract and managed by community voting.
    
4.  Trusted Instances: Community votes determine which backend instances are trusted, enhancing security and reliability.
    

## Uberscript System

The uberscript system allows users to completely override the UI of supported websites based on community-created designs. There are two types of uberscripts:

1.  Default Uberscripts: These are high-quality, community-vetted UI overrides installed automatically for all users. Default uberscripts are selected based on community votes and ensure a standardized experience for popular websites.
    
2.  Optional Uberscripts: Users can browse and select optional uberscripts for additional customization or specialized use cases. Optional uberscripts allow users to personalize their experience on specific sites, with community feedback and votes influencing their quality and popularity.
    

An algorithm categorizes and ranks uberscripts, allowing users to find the “Most Popular Ever” and “Most Popular Now” scripts based on karma scores and community engagement.

## Technical Details

### Smart Contract Design

1.  Instance Registration: Each backend instance registers with the smart contract to be recognized by the network.
    
2.  Karma Management:
    

-   Users earn karma for accurate and high-quality contributions.
    
-   Karma is spent when voting to upvote or downvote flagged content, trusted instances, and uberscripts.
    

4.  Voting Logic:
    

-   Voting power is weighted by karma, incentivizing useful contributions.
    
-   Community voting maintains a list of trusted instances, improving network reliability.
    

6.  Trusted Instances:
    

-   Community votes decide which instances appear in the trusted list.
    
-   Higher-karma users have greater influence on instance reliability, ensuring a self-regulating system.
    

### Frontend (Browser Plugin)

The Decentralized Content Filter browser plugin is open-source and designed for maximum user customization. It allows users to choose how different types of flagged content are handled, including options to:

-   Block content entirely.
    
-   Hide content partially or fully.
    
-   Gray out content to indicate low trustworthiness.
    
-   Mark content with icons or labels to show karma or warning levels.
    
-   Display karma scores as a metric of community judgment.
    

Additionally, the plugin includes:

-   Content Preferences: Users can specify which types of content they want to block, hide, or display.
    
-   Content Browsing: An algorithm ranks and categorizes content, providing options to browse the “Most Popular Ever” and “Most Popular Now” content based on karma scores and community engagement.
    

### Backend Server Package (Instances)

1.  Self-Hosted Backend:
    

-   Users can download a “server” package to host their own backend instance, reducing their reliance on public instances.
    
-   Each instance periodically syncs data via the smart contract ledger.
    
-   Instance Availability: Users have the option to self-host or to purchase a pre-configured instance hosted on platforms like S3 (with plans to expand to other platforms in the future).
    

3.  Public Port Requirement:
    

-   To contribute actively to the network and earn extra karma, instances must open a public port for the backend interface. This allows the instance to serve as a part of the community network, enabling data sharing and contributing to decentralized filtering.
    

5.  JSON-Based API:
    

-   Instances serve JSON data to plugins, ensuring lightweight and straightforward communication.
    

7.  Ledger Syncing:
    

-   The server syncs with the blockchain ledger to retrieve the trusted instances list and update content flags.
    

## Governance and Karma System

-   Karma Donations: The system operates on donations in the form of karma, allowing users to support ongoing development and sustainability.
    
-   Karma Decay: Karma decays over time if unused, preventing hoarding and encouraging active participation.
    
-   User Rewards: High-contribution users may receive bonus karma, promoting continued engagement and reliable contributions.
    

## User Incentives and Sustainability Model

1.  Virtually Free for End Users: The system remains free for plugin users, who connect to backend instances without incurring transaction fees.
    
2.  Donation-Based Funding: Karma donations help fund the smart contract and keep the project running.
    
3.  Proportional Rewards: As the contract’s balance increases, karma rewards adjust proportionally to incentivize long-term participation.
    

# Roadmap

## Phase 1: Research and Initial Design

1.  Market and Technical Research:
    

-   Research similar projects to understand best practices in decentralized content moderation and uberscript customization.
    
-   Investigate blockchain platforms (e.g., Ethereum, Polygon) to determine the most cost-effective and scalable platform for smart contract deployment.
    

3.  Feature and Requirements Definition:
    

-   Outline requirements for core functionalities, including user submissions, voting, karma management, and uberscripts.
    
-   Define initial structure and permissions for backend instances, smart contract functionality, and plugin customization.
    

5.  Tokenomics and Governance Model:
    

-   Design a karma system that supports contribution rewards, spending, and decay.
    
-   Define governance policies, particularly around voting for trusted instances and uberscripts, to maintain high-quality content filtering.
    

## Phase 2: Smart Contract Development and Testing

1.  Develop Smart Contract (Blockchain Backend):
    

-   Create a smart contract that manages instance registration, karma accumulation, voting, and the list of trusted instances.
    
-   Implement support for voting on default uberscripts to be installed automatically and optional uberscripts users can install manually.
    

3.  Test on Blockchain Testnet:
    

-   Deploy the smart contract on a testnet for initial testing, including cost estimation and functionality validation.
    
-   Gather early feedback on contract functionality to make adjustments for efficiency and usability.
    

5.  Security Audit:
    

-   Perform a third-party audit to ensure the smart contract is secure.
    
-   Address audit feedback and retest on the testnet as needed.
    

## Phase 3: Backend Instance and Uberscript System Development

1.  Backend Server Package Development:
    

-   Build a backend instance package capable of syncing with the smart contract and providing data to the browser plugin via a JSON API.
    
-   Implement public port functionality to allow instances to serve as part of the community network and earn karma.
    

3.  Uberscript System for UI Override:
    

-   Develop a system for uberscripts, with initial templates to demonstrate how users can override website UIs.
    
-   Implement community voting for uberscripts to determine which will be installed by default and which are optional.
    

5.  Setup Self-Hosting and S3 Instance Options:
    

-   Develop documentation and automated scripts for setting up self-hosted backend instances.
    
-   Prepare a pre-configured S3 instance package for users who want a simpler setup option.
    

## Phase 4: Browser Plugin and User Interface Development

1.  Browser Plugin Core Development:
    

-   Design the plugin’s interface, including options for filtering content, displaying karma, and applying uberscripts.
    
-   Integrate functionality for users to enable default uberscripts and browse/install optional uberscripts.
    

3.  User Customization Features:
    

-   Develop features for users to specify content handling preferences (e.g., block, hide, gray out, or mark).
    
-   Add sorting options for browsing “Most Popular Ever” and “Most Popular Now” uberscripts based on community votes.
    

5.  Plugin Testing and Feedback:
    

-   Conduct initial testing with a sample backend instance and smart contract on testnet.
    
-   Gather feedback on the UI and user experience for improvements before the beta release.
    

## Phase 5: Beta Release and Community Testing

1.  Beta Testing:
    

-   Release a beta version of the plugin, backend instance package, and smart contract on the testnet for community testing.
    
-   Document and prioritize issues, feature requests, and user feedback.
    

3.  Documentation and Community Support:
    

-   Prepare comprehensive guides for setting up instances, using the plugin, and contributing uberscripts.
    
-   Onboard early community members to run instances and participate in voting for uberscripts.
    

5.  Bug Bounty Program:
    

-   Launch a bug bounty program to test smart contract security, backend reliability, and plugin stability in preparation for the mainnet.
    

## Phase 6: Mainnet Launch and Scaling

1.  Mainnet Deployment:
    

-   Deploy the audited and tested smart contract to the mainnet.
    
-   Release the backend instance and plugin with full mainnet support.
    

3.  Community Launch and Marketing:
    

-   Execute a community launch to promote the project’s goals and encourage adoption.
    
-   Partner with decentralization and privacy communities to build awareness and attract contributors.
    

5.  Ongoing Governance and Uberscript Management:
    

-   Begin the community-led selection of default uberscripts and encourage contributions of optional uberscripts.
    
-   Set up a review and voting schedule for uberscript updates, instance trustworthiness, and project enhancements.
    

7.  Future Expansions:
    

-   Explore potential integration with decentralized storage networks for enhanced content delivery.
    
-   Investigate partnerships with websites willing to expose JSON endpoints to facilitate JSON-first website rendering.
    
-   Develop APIs and SDKs to expand compatibility across mobile, desktop, and alternative platforms.
    
