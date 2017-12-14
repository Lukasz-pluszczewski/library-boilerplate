# Library boilerplate
> NPM library boilerplate using Rollup, ES6 (with Babel), ESLint, Mocha

Library boilerplate using rollup for bundling, babel for transpiling to ES5, ESlint for linting and mocha/chai/sinon stack for tests that makes it easy and fast to make your own NPM plugin for use both in Node.js and browser environment.

## Usage

#### Make it your own
* remove .git directory (with `rm -rf .git` command)
* Rename all `library-boilerplate` and in `rollup.config.js` in package.json to name of your library
* Change author and/or licence as well as the repo url in package.json
* Change author name in LICENCE file

#### Add exports in src/index.js
You can import export whatever you want using es2015 default or named exports as you need
```javascript
// src/index.js
import myCoolLib from './myCoolLib.js';

export const somethingElse = myCoolLib.somethingElse; 

export default myCoolLib;

// then the use of this library
import myCoolLib, { somethingElse } from 'nameOfMyCoolLib';
```

#### Install dependencies
```bash
npm i
```

#### Run linter
```bash
npm run lint
```

#### Run tests
Tests should be added in `test` directory
```bash
npm run test
```

#### To build the project
It will be done automatically before npm publish to prevent you from publishing library without bundled files or out-dated bundle
```bash
npm run build
```
This will create lib directory with UMD and ES2015 versions of minified bundles

#### CI
There is very simple circle.yml configuration file for CircleCI (ver 2). Feel free to use it or just remove it.

## FAQ
#### Why have you disabled package-lock.json?
It seems that package-lock mechanism is still broken (e.g. https://github.com/npm/npm/issues/17091 among others). I had many issues with it (including strange changes in package-lock every time I run `npm i`) so I decided to just stick to `save-exact` setting for now

#### How can I customize babel settings?
You can modify .babelrc file to change, among other things, target browsers (see [babel-preset-env documentation](https://github.com/babel/babel/tree/master/packages/babel-preset-env) to learn more)

#### Why this exists?
There are some library boilerplates out there but they have some or all of the following issues:
* using Grunt/Gulp as unnecessary layer of abstraction. Except very complex cases [NPM scripts is all you need](https://www.keithcirkel.co.uk/why-we-should-stop-using-grunt/)
* lacking transpiling capabilities (often you have ES2015 out of the box but you will struggle with adding e.g. stage-0 - in case of rollup)
* not clearly explained what should be exported where, if you can import the built library as ES2015 module etc.
* tests environment not configured
* no bundler included

#### Are there good alternatives?
Yes and you should definitely check them out:
* [es6-npm-module](https://github.com/ghaiklor/generator-es6-npm-module) yeoman generator that is worth trying
* [es6-library-boilerplate](https://github.com/CurtisHumphrey/es6-library-boilerplate) boilerplate for frontend libraries with a lot of features

#### I found a bug! What should I do?
There are at least 3 options:
1. Add an issue, write test(s) for bug you found, write fix that will make your test(s) pass, submit pull request
2. Add an issue, write test(s) for bug you found, submit pull request with you test(s)
3. Add an issue