## Installation
Node is best installed under a version manager, node version manager.
### Upgrading NPM
`npm install -g npm@latest`

### [NVM (Windows)](https://github.com/coreybutler/nvm-windows)
* On windows if node was previously installed nvm might not have the correct permissions to inject another node version.  
install from chocolatey
`cinst install nvm -y`
#### Usage: 
* `nvm install <version>|latest`
* `nvm uninstall <version>`
* `nvm use`

### [NVM (Linux)](https://github.com/nvm-sh/nvm)
install with bash script
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash`
#### Usage: 
* `nvm install --lts`
* `nvm uninstall <version>`
* `nvm use`


## NPM
## Sorted by category

### User Managment

|command|description|
|---|---|
|`npm access`|Set access level on published packages|
|`npm adduser`|Add a registry user account|

### Development Assistance

### Project Managment

|command|description|
|---|---|
|[`npm audit`](https://docs.npmjs.com/cli/v6/commands/npm-audit)|Scan your project for vulnerabilities and automatically install any compatible updates to vulnerable dependencies|
|`npm bin`|Print the folder where npm will install executables.|


|command|description|
|---|---|  
|`npm bugs`|Bugs for a package in a web browser maybe|  
|`npm build`|Build a package|  
|`npm bundle`|Removed|  
|`npm cache`|Manipulates packages cache|  
|`npm ci`|Install a project with a clean slate|  
|`npm completion`|Tab completion for npm|  
|`npm config`|Manage the npm configuration files|  
|`npm dedupe`|Reduce duplication|  
|`npm deprecate`|Deprecate a version of a package|  
|`npm dist-tag`|Modify package distribution tags|  
|`npm docs`|Docs for a package in a web browser maybe|  
|`npm doctor`|Check your environments|  
|`npm edit`|Edit an installed package|  
|`npm explore`|Browse an installed package|  
|`npm fund`|Retrieve funding information|  
|`npm help`|Search npm help documentation|  
|`npm help-search`|Get help on npm|  
|`npm hook`|Manage registry hooks|  
|`npm init`|Create a package.json file|  
|`npm install`|Install a package|  
|`npm install-ci-test`|Install a project with a clean slate and run tests|  
|`npm install-test`|Install package(s) and run tests|  
|`npm link`|Symlink a package folder|  
|`npm logout`|Log out of the registry|  
|`npm ls`|List installed packages|  
|`npm org`|Manage orgs|  
|`npm outdated`|Check for outdated packages|  
|`npm owner`|Manage package owners|  
|`npm pack`|Create a tarball from a package|  
|`npm ping`|Ping npm registry|  
|`npm prefix`|Display prefix|  
|`npm profile`|Change settings on your registry profile|  
|`npm prune`|Remove extraneous packages|  
|`npm publish`|Publish a package|  
|`npm rebuild`|Rebuild a package|  
|`npm repo`|Open package repository page in the browser|  
|`npm restart`|Restart a package|  
|`npm root`|Display npm root|  
|`npm run-script`|Run arbitrary package scripts|  
|`npm search`|Search for packages|  
|`npm shrinkwrap`|Lock down dependency versions for publication|  
|`npm star`|Mark your favorite packages|  
|`npm stars`|View packages marked as favorites|  
|`npm start`|Start a package|  
|`npm stop`|Stop a package|  
|`npm team`|Manage organization teams and team memberships|  
|`npm test`|Test a package|  
|`npm token`|Manage your authentication tokens|  
|`npm uninstall`|Remove a package|  
|`npm unpublish`|Remove a package from the registry|  
|`npm update`|Update a package|  
|`npm version`|Bump a package version|  
|`npm view`|View registry info|  
|`npm whoami`|Display npm username|  
