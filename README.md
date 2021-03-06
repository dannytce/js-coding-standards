# JavaScript Coding Standards

> Write bulletproof JavaScript like a pro! 😎

[![Build Status][travis-badge]][travis-url]
![ESLint version][eslint-version]


## About

This repository contains various configuration files for the awesome JavaScript linter, [ESLint][eslint-url]. The configuration files are purposefully separated into various categories to allow their composition according to developers' preferences or requirements. It should also make adoption of ESLint across existing codebases easier.

## Goals

- **Safety**
- **Coding style consistency**

The goal of this project is to help all developers write better code. It should not be a hindrance or cause a major fight about how to write it. Although it will never achieve the "one-config-suits-all" status in terms of coding style, it should achieve that when it comes to writing safe JavaScript.

## Usage

### Installation

This package can be installed via npm:

`npm install --save-dev @strv/eslint-config-javascript`

### Configuration

Once the ruleset is installed, you must create your own *.eslintrc.{js,json,yml}* configuration file in your project's root and include those rulesets that you want to use. See the [examples](examples) directory for, well... examples.

> **WARNING:** The order in which various configuration files are loaded **DOES MATTER**. The recommended load order is the following:
>
> - One of the versioned configurations for the chosen environment, ie. *environments/nodejs/v6*
> - The best practices configuration file (if it exists), ie. *environments/nodejs/best-practices*
> - The optional configuration file (if it exists), ie. *environments/nodejs/optional*
> - Coding style ruleset, ie. *coding-styles/base*

### Example configuration file

Here is an example *.eslintrc.js* configuration file. You can copy/paste it into your project, if you like.

```js
'use strict'

module.exports = {
  extends: [
    // Include configuration for working with Node.js source code
    '@strv/javascript/environments/nodejs/v6',
    '@strv/javascript/environments/nodejs/best-practices',
    '@strv/javascript/environments/nodejs/optional',
    // Include coding style configuration. This does not depend on
    // any of the above and should be included last.
    '@strv/javascript/coding-styles/base'
  ]
}
```

## Structure

The ESLint rules are semantically grouped into various categories for easy composition.

### [Environments](environments)

These rules are the ones you should be including in your *.eslintrc.{js,json,yml}* configuration. They are separated into categories based on the environment for which the code is being developed. Additionally, each environment provides several levels of "strictness" which the developer can choose from. This level of separation is meant as a means to gradual adoption of **all the rulesets**.

> It is recommended for new projects to include all levels.

### [Coding Styles](coding-styles)

These rules help developers adhere to a certain coding style. They do not provide code safety, but help developers write code in a way that is consistent across the whole codebase, which in long term helps them better maintain that code.

These rules are intended to be used independently on platform. However, you should still consider including rules for your environment if you really care about high-quality JavaScript.

## License

This software is licensed under the **BSD-3-Clause License**. See the [LICENSE](LICENSE) file for more information.


[eslint-url]: http://eslint.org
[travis-badge]: https://travis-ci.org/strvcom/js-coding-standards.svg
[travis-url]: https://travis-ci.org/strvcom/js-coding-standards
[eslint-version]: https://img.shields.io/badge/ESLint->=3.2.0-brightgreen.svg
