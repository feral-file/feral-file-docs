# Feral File Documents Repository

## Overview
This repository holds documentation files used by the Feral File mobile app and TV display app: agreements, configurations, and app content.

The website's Learn, About, FAQ and legal pages are not here. They live in `feral-file/ff3` (`data/content/learn/`, `data/content/legal/`) and ship with the site's releases.

## Impact on Production
Two branches are read in production, by different clients:
- **`main`**: every FF1 reads `configs/display.json` (FF OS builds bake `PUB_DOC_URL=https://raw.githubusercontent.com/feral-file/feral-file-docs/main`, a variable in `feral-file/ffos`).
- **`master`**: the store app reads `app/` (`PUBDOC_URL` in ff-app's `ENV_VARS` secret is `https://raw.githubusercontent.com/bitmark-inc/feral-file-docs/master` in 1.8.33). `app/version_compatibility.json` exists only on `master`; an edit to `app/` on `main` does not reach the app.

**Developers must be informed when adding new files** so they can include them in the data loading process for the app or the player.

## Repository Structure

### **1. agreements/**
Legal and policy documents. The store app (1.8.33) loads its EULA and privacy policy from `feral-file/ff-app-docs` (`FERALFILE_DOCS_URL`); the `ff-app-eula` and `ff-app-privacy` copies here are identical and stay for older installs. Nothing in the feral-file org's code reads the others (`ff-app-data-usage`, `ff-artist-group-exhibition`, `ff-artist-solo-exhibition`, `ff-artist-migration`, `ff-exhibition-curator`, `ff-collector-rights`).

### **2. app/**
Read by the **Feral File app** from the `master` branch (see above), including:
- `release-note.md` - Release notes for the app.
- `security.md` - Security-related documentation.
- **Source exhibition data** - Contains structured data for exhibitions displayed in the app.
- `version.json` - Tracks the versioning details of the app.

### **3. configs/**
This folder contains JSON configuration files that are used by:
- **Mobile App**
- **TV Display App**

These files define app settings and behaviors for different environments.

## Maintenance Notes
- **agreements/**: Updates to policies or agreements should be reviewed before deployment.
- **app/**: Only the Feral File app dev team is working on this.
- **configs/**: Changes here affect mobile and TV applications, requiring careful testing.

For any structural changes, ensure that dependencies across the apps are considered before modifying this repository.
