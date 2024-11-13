# Decentralized Content Filter - Opera Plugin Developer Guide

## Table of Contents
1. [Overview](#overview)
2. [Opera-Specific Integration Details](#opera-specific-integration-details)
3. [Installation and Testing](#installation-and-testing)
4. [Deployment on Opera Add-ons](#deployment-on-opera-add-ons)

---

## Overview
This guide provides Opera-specific instructions for implementing the Decentralized Content Filter plugin. Opera's extension system is largely compatible with Chrome’s, but there are unique settings and testing methods specific to Opera’s platform.

---

## Opera-Specific Integration Details

1. **manifest.json Adjustments**
   - **Compatibility Key**: Add `"applications": { "opera": { "id": "plugin@opera.com" } }` to specify Opera compatibility and ensure smooth installation.
   - **Permissions**: Similar to Chrome, but Opera may have stricter enforcement of `activeTab` and web request permissions.

2. **Background Script Handling**
   - Opera uses Chrome-like background pages in `manifest_version: 2`, so no adjustments are needed if using Chrome’s extension model.
   - **Event Handling**: Use `chrome.runtime.onMessage` for compatibility with Opera's handling of background scripts.

3. **Declarative Net Request API**
   - Opera supports the `declarativeNetRequest` API from Chrome, enabling efficient content blocking and filtering. Configure `declarativeNetRequest` rules in `manifest.json` as in Chrome.

---

## Installation and Testing

1. **Loading the Unpacked Extension**
   - Go to `opera://extensions`, enable “Developer mode,” and click “Load unpacked.” Select the plugin directory.
   - Test the plugin’s features, especially focusing on compatibility with Opera’s interface.

2. **Testing Permissions**
   - Opera may prompt for permissions more strictly, especially `declarativeNetRequest` and `activeTab`. Confirm these are functional and avoid unnecessary permissions.

---

## Deployment on Opera Add-ons

1. **Packaging**
   - Opera accepts `.crx` files from Chrome builds, so you can use the same build process as for Chrome, or directly upload the `.zip` file.

2. **Submission to Opera Add-ons**
   - Create an account on the Opera Add-ons site and submit the extension file (either `.zip` or `.crx`).
   - Opera may review extensions based on Chrome Web Store permissions, so ensure only necessary permissions are included.

This guide provides Opera-specific adjustments for compatibility and deployment, leveraging similarities to Chrome while following Opera’s unique testing and permission requirements.
