## @haaretz/commitlint-config

Shareable commitlint config enforcing the Haaretz commit convention (mostly 
[angular](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit), 
but a bit more relaxed). 

For use with [@commitlint/cli](https://www.npmjs.com/package/@commitlint/cli) 
and [@commitlint/prompt-cli](https://www.npmjs.com/package/@commitlint/prompt-cli).

This configuration checks every commit message to ensure it complies with the following structure:
```git
type(scope)?: subject line

body?

footer?
```
The following rules must too be observed:

* The header (first line) length is no more than `100` chars at length (warning)
* The header starts with the `type` of commit at hand. Options are:
  * `build` Build-process related commits.
  * `chore` Maintenance. General chores that don't fall into any of the other categories
  * `ci` Continuous-integration related commits (e.g., fixing Travis build, setting up Jenkins, etc.)
  * `docs` Documentation related commits
  * `feat` Commits introducing a new feature
  * `fix` Bug fixes
  * `perf` Commits dealing with measuring or improving performance
  * `refactor` Refactor commits that introduce no new functionality, infrastructure or fixes.
  * `revert` Reverting an old commit 
  * `style` Reformatting, missing commas, semi colons, etc.
  * `test` When _only_ adding missing or fixing failing tests
* The `type` must be lower-case
* The header _may_ include a `scope` denoting what parts of the code are affected by the changes
* The scope must be enclosed in parentheses
* The `scope` must be lower-case
* The `type` and optional `scope` must be followed directly by a colon (`:`) and a space
* The header must include a subject succinctly describing the commit
* The subject must not end with a `.`
* There is a blank line between the commit-msg header and body, if one exists
* There is a blank line between the commit-msg body and footer, if one exists

## Installaion
Install with Yarn:
```sh
yarn add --dev @haaretz/commitlint-config
echo "module.exports = {extends: ['@haaretz/commitlint-config']};" > commitlint.config.js
```
or with npm:
```sh
npm install -save-dev @haaretz/commitlint-config
echo "module.exports = {extends: ['@haaretz/commitlint-config']};" > commitlint.config.js
```

## Usage
Install `husky` and `@commitlint/cli`:
```sh
yarn add --dev @commitlint/cli husky
```

And add a `commitmsg` script to your `package.json`:
```json
"scripts": {
  "commitmsg": "commitlint -e"
  }
```

Husky will setup a `commitmsg` git-hook that is executed every time a new commit 
is created, invoking commitlint with the -e flag, which causes it process the 
commit message from `.git/COMMIT_MSG`.
