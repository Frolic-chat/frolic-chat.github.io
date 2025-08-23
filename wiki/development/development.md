---
title: Development Details
layout: default
excerpt: How to set up a development environment to help with testing and running unreleased versions
---
# Development & Best Practices
This page describes how to set up a development environment to help with testing and running unreleased versions of Frolic.

## Code of Conduct
Read our [Code of Conduct](CODE_OF_CONDUCT.html) to see if your development goals align with Frolic's.

## Development
The NodeJS version used by Frolic is locked to the Electron version and is currently `22.x`. Having a system node of a higher version probably won't hurt anything. There are tools like `nvm` to manage your node version if you feel it might be an issue.

```bash
# Windows only:
npm install --global --production --vs2015 --add-python-to-path yarn node-gyp

# Ubuntu only:
sudo apt install libsecret-1-dev

# MacOS only:
brew install python-setuptools

# All operating systems:
git clone https://github.com/Frolic-chat/Frolic.git
cd Frolic
yarn

# Optional: make your commits anonymous
git config --local user.name "SOME NAME"
git config --local user.email "some@email.com"
```

### Development Mode
While making changes, you can have your changes tested in real time by running two processes simultaneously:

##### #1: yarn watch
```bash
yarn watch
```
This will start real-time monitoring of file changes and rebuild changed codepaths, allowing you to check for many common code errors in real time.

##### #2 yarn start
```bash
yarn start
# Use `Ctrl+Shift+I` to open the Chromium developer tools.
```
This will launch the version of the app compiled by `yarn watch`, allowing you to log in and verify that everything is working correctly. It accepts common electron launch parameters like `--pasword-store=...` as well as the custom `--devtools` to launch the Chromium developer tools in their own windows.

### Build
```bash
cd electron

yarn build:dist
node pack.js
```

#### Build Failure Troubleshooting
Unusual behavior while building can be caused by artifacts from past build failures.

Removing or renaming these directories is a good first-step to troubleshooting:
* `frolic/electron/app` - This folder will be recreated by `yarn watch` or `yarn build:dist`
* `frolic/electon/dist` - **Ensure** you've recovered any compiled builds you want to keep. This folder will be recreated by `node pack.js` or `yarn pack-all`

If you encounter error 'Could not detect abi for version X.X.X and runtime electron', try running:
```bash
npx uuaw node-abi
```

## Dependencies
Note: Do not add or upgrade dependencies. If you feel there's necessary upgrade, file an issue report and a discussion on the merits will ensue. Frequently, module upgrades cause undocumented behavior changes that can disturb the app and have to be tested at length. That's why `yarn.lock` exists and is version controlled.

To upgrade NPM dependencies, run `yarn upgrade` locally. Run `yarn outdated` to see pending upgrades.
