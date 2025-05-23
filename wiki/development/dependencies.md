---
title: Dependencies & Why
layout: default
excerpt: What is each dependency there for?
---
# Abstract
Dependencies add addtional layers of complexity for little benefit.

Their undocumented use can lead to a build up of dependencies with little to no actual benefit to the project.

This document aims to clarify why any dependency is included so this reasoning can be reexamined later to see if the dependency is still relevant.

---
Dependencies will be listed in alphabetical order when lack of better way can be found.

### Lodash
Lodash is an outdated depdency that's been replaced by core js functions and it should be removed as soon as possible. Pruning a file of lodash so it can be removed as an import is a worthwhile endeavour.

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

## Dependencies for Use Cases
These deps were added with a specific purpose.

* @types/webpack-env

  This was added to resolve editor warnings using require.context in main.ts - but it's no longer necessary due to refactoring.
