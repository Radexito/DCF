# Decentralized Content Filter - Firefox Plugin Developer Guide

## Table of Contents
1. [Overview](#overview)
2. [Firefox-Specific Integration Details](#firefox-specific-integration-details)
3. [Installation and Testing](#installation-and-testing)
4. [Deployment on Firefox Add-ons (AMO)](#deployment-on-firefox-add-ons-amo)

---

## Overview
This guide provides Firefox-specific instructions for implementing the Decentralized Content Filter plugin using the WebExtensions API. Firefox has strong compatibility with the WebExtensions standard, making the plugin development similar to other Chromium-based browsers but with a few Firefox-specific considerations.

---

## Firefox-Specific Integration Details

1. **manifest.json Adjustments**
   - **Browser Compatibility Key**: Add `"applications": { "gecko": { "id": "plugin@example.com", "strict_min_version": "91.0" } }` to specify compatibility with Firefox and the minimum version required.
   - **Permissions**: Firefox may require additional permissions to manage web requests, so ensure all permissions are explicitly defined.

2. **Background Script Configuration**
   - **Event Handling**: Firefox may treat background events differently. Use `browser.runtime.onMessage` for inter-component messaging, as this has broader compatibility across Firefox versions than `chrome.runtime.onMessage`.

3. **Storage API**
   - **Local Storage**: Firefox treats `browser.storage.local` storage quotas differently than Chrome, so for large datasets, consider using IndexedDB.
   - **Sync API**: Firefox supports `browser.storage.sync`, which allows data to be synced across devices. This may be useful for syncing user preferences or instance settings.

4. **Content Security Policies (CSP)**
   - Firefox enforces strict CSPs. Ensure all remote script or stylesheet injections align with Firefox’s CSP requirements. Use `browser.runtime.getURL` to load resources included in the extension package securely.

---

## Installation and Testing

1. **Loading the Unpacked Extension**
   - Go to `about:debugging`, select “This Firefox” > “Load Temporary Add-on,” and choose the `manifest.json` file in the plugin directory.
   - Test core features, including content filtering, voting, karma display, and uberscript application, directly within Firefox Developer Edition for optimal debugging tools.

2. **Testing Permissions**
   - Firefox may require re-confirming permissions, especially for web request and storage APIs. Ensure permissions are explicitly requested and check `about:addons` to confirm permissions are enabled.

---

## Deployment on Firefox Add-ons (AMO)

1. **Packaging**
   - Run `web-ext build` to package the plugin as an `.xpi` file for Firefox.
   - Validate the package with `web-ext lint` to identify any potential compatibility or security issues.

2. **Submission to AMO**
   - Create a developer account on AMO and submit the `.xpi` file for review.
   - Firefox may enforce additional manual review steps; ensure all required fields are completed, especially regarding permissions and privacy practices.

This guide ensures smooth integration with Firefox-specific policies, storage handling, and deployment on the Firefox Add-ons platform.
