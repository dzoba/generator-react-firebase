# react-firebase

[![NPM version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url]
[![Dependency Status][daviddm-image]][daviddm-url]
[![Code Coverage][coverage-image]][coverage-url]
[![Code Climate][climate-image]][climate-url]
[![License][license-image]][license-url]
[![Code Style][code-style-image]][code-style-url]

## Table of Contents
1. [Features](#features)
1. [Requirements](#requirements)
1. [Getting Started](#getting-started)
1. [Application Structure](#application-structure)
1. [Development](#development)
  1. [Routing](#routing)
1. [Testing](#testing)
1. [Configuration](#configuration)
1. [Production](#production)
1. [Deployment](#deployment)

## Requirements
* node `^5.0.0`
* yarn `^0.23.0` or npm `^3.0.0`

## Getting Started

1. Install dependencies: `yarn` or `npm install`

2. Start Development server: `yarn start` or `npm start`

While developing, you will probably rely mostly on `npm start`; however, there are additional scripts at your disposal:

|`npm run <script>`    |Description|
|-------------------|-----------|
|`start`            |Serves your app at `localhost:3000`|
|`build`            |Builds the application to ./dist|
|`test`             |Runs unit tests with Karma. See [testing](#testing)|
|`test:watch`       |Runs `test` in watch mode to re-run tests when changed|
|`lint`             |[Lints](http://stackoverflow.com/questions/8503559/what-is-linting) the project for potential errors|
|`lint:fix`         |Lints the project and [fixes all correctable errors](http://eslint.org/docs/user-guide/command-line-interface.html#fix)|

## Application Structure

The application structure presented in this boilerplate is **fractal**, where functionality is grouped primarily by feature rather than file type. Please note, however, that this structure is only meant to serve as a guide, it is by no means prescriptive. That said, it aims to represent generally accepted guidelines and patterns for building scalable applications. If you wish to read more about this pattern, please check out this [awesome writeup](https://github.com/davezuko/react-redux-starter-kit/wiki/Fractal-Project-Structure) by [Justin Greenberg](https://github.com/justingreenberg).

```
.
├── build                    # All build-related configuration
│   └── create-config        # Script for building config.js in ci environments
│   └── karma.config.js      # Test configuration for Karma
│   └── webpack.config.js    # Environment-specific configuration files for webpack
├── server                   # Express application that provides webpack middleware
│   └── main.js              # Server application entry point
├── src                      # Application source code
│   ├── index.html           # Main HTML page container for app
│   ├── main.js              # Application bootstrap and rendering
│   ├── normalize.js         # Browser normalization and polyfills
│   ├── components           # Global Reusable Presentational Components
│   ├── containers           # Global Reusable Container Components
│   ├── layouts              # Components that dictate major page structure
│   │   └── CoreLayout       # Global application layout in which to render routes
│   ├── routes               # Main route definitions and async split points
│   │   ├── index.js         # Bootstrap main application routes with store
│   │   └── Home             # Fractal route
│   │       ├── index.js     # Route definitions and async split points
│   │       ├── assets       # Assets required to render components
│   │       ├── components   # Presentational React Components
│   │       ├── container    # Connect components to actions and store
│   │       ├── modules      # Collections of reducers/constants/actions
│   │       └── routes **    # Fractal sub-routes (** optional)
│   ├── static               # Static assets
│   ├── store                # Redux-specific pieces
│   │   ├── createStore.js   # Create and instrument redux store
│   │   └── reducers.js      # Reducer registry and injection
│   └── styles               # Application-wide styles (generally settings)
├── project.config.js        # Project configuration settings (includes ci settings)
└── tests                    # Unit tests
```

## Development

### Routing
We use `react-router` [route definitions](https://github.com/ReactTraining/react-router/blob/v3/docs/API.md#plainroute) (`<route>/index.js`) to define units of logic within our application. See the [application structure](#application-structure) section for more information.

## Testing
To add a unit test, create a `.spec.js` file anywhere inside of `./tests`. Karma and webpack will automatically find these files, and Mocha and Chai will be available within your test without the need to import them.

## Production

Build code before deployment by running `npm run build`. There are multiple options below for types of deployment, if you are unsure, checkout the Firebase section.

### Deployment

1. Login to [Firebase](firebase.google.com) (or Signup if you don't have an account) and create a new project
2. Install cli: `npm i -g firebase-tools`
3. Login: `firebase login`
4. Initialize project with `firebase init` then answer:
  * What file should be used for Database Rules?  -> `database.rules.json`
  * What do you want to use as your public directory? -> `build`
  * Configure as a single-page app (rewrite all urls to /index.html)? -> `Yes`
  * What Firebase project do you want to associate as default?  -> **your Firebase project name**
5. Build Project: `npm run build`
6. Confirm Firebase config by running locally: `firebase serve`
7. Deploy to firebase: `firebase deploy`
**NOTE:** You can use `firebase serve` to test how your application will work when deployed to Firebase, but make sure you run `npm run build` or `npm run build:prod` first.

[npm-image]: https://img.shields.io/npm/v/react-firebase.svg?style=flat-square
[npm-url]: https://npmjs.org/package/react-firebase
[travis-image]: https://img.shields.io/travis/testuser/react-firebase/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/testuser/react-firebase
[daviddm-image]: https://img.shields.io/david/testuser/react-firebase.svg?style=flat-square
[daviddm-url]: https://david-dm.org/testuser/react-firebase
[climate-image]: https://img.shields.io/codeclimate/github/testuser/react-firebase.svg?style=flat-square
[climate-url]: https://codeclimate.com/github/testuser/react-firebase
[coverage-image]: https://img.shields.io/codeclimate/coverage/github/testuser/react-firebase.svg?style=flat-square
[coverage-url]: https://codeclimate.com/github/testuser/react-firebase
[license-image]: https://img.shields.io/npm/l/react-firebase.svg?style=flat-square
[license-url]: https://github.com/testuser/react-firebase/blob/master/LICENSE
[code-style-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[code-style-url]: http://standardjs.com/
