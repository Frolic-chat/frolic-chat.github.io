---
title: Dependencies & Why
layout: default
excerpt: What is each dependency there for?
---
# Abstract
Dependencies add additional layers of complexity for little benefit.

Their undocumented use can lead to a build up of dependencies with little to no actual benefit to the project.

This document aims to clarify why any dependency is included so this reasoning can be reexamined later to see if the dependency is still relevant.

---
Dependencies will be listed in alphabetical order when lack of better way can be found.

## Likely Firm
These dependencies could be replaced with better alternatives, but until there's a real upgrade, there's no reason thinking about it.
* Axios
* Dart Sass

## Core Dependencies
These dependencies will never be going away; they're too ingrained in core functionality.
* Bootstrap
* Electron
* Fontawesome
* Nodejs
* Vuejs
* Webpack
* electron-log

## Peer dependencies of core
These deps are peers of the installed core frameworks and can't be removed without reducing functionality.
* Popper.js

## Dependencies for Use Cases
These deps were added with a specific purpose.

### `semver`
Semver enables Frolic to perform version-dependent upgrades. You can create a routine in `./electron/version-upgrade.ts` named as a version and it will be executed when upgrading to that version or higher. This could not be done without semantic version comparisons and sorting from `semver`.

Being able to execute code only on upgrade is particularly useful for shepherding users through structural changes.

### `qs`
"qs" - short for Query String - serializes data into a URL compatible query string. While this is useful for sending data to servers, this is also useful for any place where we can only rely on string-based communications. (Could be very useful for arbitrary data comm over F-Chat in particular.)

An alternative to qs is the modern builtin URLSearchParams type.

### `nlf`
Nlf is a tool to examine the licenses of the dependencies of your project. It's useful for the obvious reasons. :)

### Webpack Bundle Analyzer
This tool automatically opens a view of your bundles after making production build. It will let you see which modules are causing your bundle the largest size, as well as identify if there are any undesirable modules imported.

## Should Be Removed
Remove these dependencies if given the chance:
* promise-request
