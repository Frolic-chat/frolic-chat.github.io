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
The NodeJS version used by Frolic is locked to the Electron version and is currently `18.x`. Having a system node of a higher version probably won't hurt anything. The lead developer uses version 22. There are tools like `nvm` if you feel it might be an issue.

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

# Optional; make sure your commits are anonymous
git config --local user.name "SOME NAME"
git config --local user.email "some@email.com"
```

### Dev Mode
Run two processes simultaneously:

```bash
# Process 1 -- watch
cd electron
yarn watch
```

```bash
# Process 2 -- app
cd electron
yarn start
# Use `Ctrl+Shift+I` to open the Chromium debugger.
```

### Build
```bash
cd electron
yarn build:dist
node pack.js
```

#### Build Failure Troubleshooting
Unusual behavior while building can be caused by artifacts from past build failures.
Removing or renaming these directories is a good first-step to troubleshooting:
* `frolic/electron/app` - This folder will be recreated by `yarn build:dist`
* `frolic/electon/dist` - **Ensure** you've recovered any compiled builds you want to keep. This folder will be recreated by `node pack.js`

## Dependencies
Note: Adding *and upgrading* dependencies should only be done with prior consideration and subsequent testing.

That's why `yarn.lock` exists and is version controlled.

To upgrade NPM dependencies, run `yarn upgrade` locally. Run `yarn outdated` to see pending upgrades.

If you encounter error 'Could not detect abi for version X.X.X and runtime electron', try running
`npx uuaw node-abi`
