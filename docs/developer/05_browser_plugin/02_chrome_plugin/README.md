# Decentralized Content Filter - Chrome Plugin Developer Guide

## Table of Contents
1. [Overview](#overview)
2. [Chrome-Specific Integration Details](#chrome-specific-integration-details)
3. [Installation and Testing](#installation-and-testing)
4. [Deployment on Chrome Web Store](#deployment-on-chrome-web-store)

---

## Overview
This guide provides Chrome-specific instructions for implementing the Decentralized Content Filter plugin. Chrome’s WebExtensions API aligns closely with the extension standards, but Chrome-specific considerations are required for optimal performance and compliance.

---

## Chrome-Specific Integration Details

1. **manifest.json Adjustments**
   - **Version Key**: Use `manifest_version: 3` for optimized performance in Chrome. This is recommended for Chrome’s new extension model, which enhances security and performance.
   - **Permissions**: Chrome often requires explicit permission declarations, especially for blocking or modifying content. Use `"declarativeNetRequest"` and `"activeTab"` permissions as needed.

2. **Service Workers in Background Scripts**
   - **Service Workers**: In `manifest_version: 3`, Chrome uses service workers instead of background pages. Adapt all background scripts to work within a service worker.
   - **Event Handling**: Use `chrome.runtime.onMessage` in the service worker to handle asynchronous communication between components.

3. **Declarative Net Request API**
   - Chrome allows content blocking through the `declarativeNetRequest` API, which can be used to filter requests more efficiently than with background scripts. Define filtering rules in `manifest.json` to improve performance.

---

## Installation and Testing

1. **Loading the Unpacked Extension**
   - Go to `chrome://extensions`, enable “Developer mode,” and click “Load unpacked.” Select the plugin directory.
   - Test functionality within Chrome to ensure compatibility, particularly with content scripts and permissions.

2. **Testing Chrome-Specific Features**
   - Confirm that content blocking works via `declarativeNetRequest` rules.
   - Ensure service workers properly handle background events without interfering with plugin performance.

---

## Deployment on Chrome Web Store

1. **Packaging**
   - Package the extension using the Chrome Web Store guidelines. Compress the extension folder (excluding any dev files) into a `.zip` file.

2. **Submission to Chrome Web Store**
   - Create a developer account on the Chrome Web Store and upload the `.zip` file.
   - Chrome reviews extensions based on permissions, so ensure that only necessary permissions are requested in `manifest.json`.

This guide covers Chrome-specific practices to ensure compatibility, performance, and smooth deployment on the Chrome Web Store.
