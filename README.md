# Feral File Documents Repository

## Overview
This repository holds documentation files used by the Feral File mobile app and TV display app: agreements, configurations, and app content.

The website's Learn, About, FAQ and legal pages are not here. They live in `feral-file/ff3` (`data/content/learn/`, `data/content/legal/`) and ship with the site's releases.

## Impact on Production
- Any changes made to existing files that are merged into the `main` branch will **directly affect the app in the PRD environment**.
- **Developers must be informed when adding new files** so they can include them in the data loading process for the app.

## Repository Structure

### **1. agreements/**
Legal and policy documents. The app's document viewer loads `ff-app-eula` and `ff-app-privacy` (`{FERALFILE_DOCS_URL}/agreements/<doc>/en_US.md`); identical copies sit in `feral-file/ff-app-docs`. Nothing in the feral-file org's code reads the others (`ff-app-data-usage`, `ff-artist-group-exhibition`, `ff-artist-solo-exhibition`, `ff-artist-migration`, `ff-exhibition-curator`, `ff-collector-rights`).

### **2. app/**
Holds various data files used by the **Feral File app**, including:
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
