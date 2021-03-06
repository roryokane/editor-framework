# Editor Framework

[Documentation](https://github.com/fireball-x/editor-framework/tree/master/docs) |
[Downloads](http://github.com/fireball-x/editor-framework/releases/) |
[Install](https://github.com/fireball-x/editor-framework#install) |
[Features](https://github.com/fireball-x/editor-framework#features)

[![Dependency Status](https://david-dm.org/fireball-x/editor-framework.svg)](https://david-dm.org/fireball-x/editor-framework)
[![devDependency Status](https://david-dm.org/fireball-x/editor-framework/dev-status.svg)](https://david-dm.org/fireball-x/editor-framework#info=devDependencies)

Editor Framework gives you power to easily write professional multi-panel desktop software in HTML5 and io.js.

The framework is based on top of [Electron](http://github.com/atom/electron) and [Polymer](http://github.com/polymer/polymer).
It is designed conforming to Electron's [main and renderer process architecture](https://github.com/atom/electron/blob/master/docs/tutorial/quick-start.md).
To make multiple window communicate easily, Editor Framework extends Electron's Ipc message API, making it easier to send and receive callback between main and renderer processes.

It is designed for fully extendibility. In the core-level ( main process ), we fulfill this by introducing a package management module and several register API. User can load or unload packages on the fly without close or restart the app. In the page-level ( renderer process ), we use HTML5 Web-Component standards and include the Polymer solution by default. User can extends the
widgets and panels, then refresh the page to apply the changes.

![screen shot](https://cloud.githubusercontent.com/assets/174891/8265547/dd7c8412-172f-11e5-90cc-b12a91a5c73c.png)

## Install

There are two ways to install and bootstrap Editor Framework:

### Clone This Repo

Enter your repo's folder, then run the following command:

```bash
# Install npm packages, the npm script will take care of other dependencies
npm install
```

### Install With NPM

You can also install Editor Framework into your app as a npm package:

```bash
# Again, npm script will take care of other dependencies
npm install editor-framework
```

**NOTE:** after npm dependencies are installed, we will run `node-gyp rebuild` against all native modules in editor-framework path. Please make sure `node-gyp` works in your command line environment. To learn more about native module building and setting up a `node-gyp` working environment, please check out:

- [node-gyp](https://github.com/TooTallNate/node-gyp)
- [Build native module for electron](https://github.com/atom/electron/blob/master/docs/tutorial/using-native-node-modules.md)
- [native-module for beginner](https://github.com/Elzair/native-module)


## Builtin Packages

The `gulp install-builtin` will install these builtin packages(this operation is covered in npm install script):

 - Developer Tools
   - [console](https://github.com/fireball-packages/console)
   - [ipc-debugger](https://github.com/fireball-packages/ipc-debugger)
   - [package-manager](https://github.com/fireball-packages/package-manager)
   - [tester](https://github.com/fireball-packages/tester)
 - Widgets
   - [ui-kit](https://github.com/fireball-packages/ui-kit)
   - [pixi-grid](https://github.com/fireball-packages/pixi-grid)

## Update

```bash
# update builtin packages and shared packages
npm run update
```

## Develop

### Test Environment

 - Mocha
 - Chai
 - Sinon

**Note:** We need to install mocha, chai in both core and page, that's why we put them in both bower and npm dependencies. The core level tests only run during develop phase, and will not go into the final product. The page level test environment has integrated with [tester](https://github.com/fireball-x/tester) package and every developer can use it to test your panels.

To test the editor-framework itself, just run:

```bash
npm test
```

### Generate Documentation

To generate the document, just run:

```bash
npm run api-core # for core-level docs
npm run api-page # for page-level docs
```

## Features

 - Package Management
   - Dynamically load and unload packages
   - Can use any web language (less, sass, coffeescript, typescript, ...) for your package, editor-framework will build it first before loading the package.
   - Watch package changes and reload or notify changes immediately
   - Manage your packages in [package manager](https://github.com/fireball-packages/package-manager)
 - Panel Management
   - Freely docks panel anywhere in multiple windows
   - Dynamically load user define panels from package
   - Easily register and respond to ipc messages for your panel
   - Easily register shortcut(hotkeys) for your panel
   - Save and load layout in json
   - Save and load panel profiles
 - Menu Extends
   - Dynamically add and remove menu item
   - Dynamically change menu item state ( enabled, checked, visible, ... )
   - Load user menu from packages
 - Commands (Under Developing)
   - Register and customize commands for your App
   - A powerful command window (CmdP) for searching and executing your commands
 - Profiles
   - Allow user to register different types of profile to their need ( global, local, project, ... )
   - Load and save profiles through unified API
 - Logs
   - Use Winston for low level logs
   - Log to file
   - Integrate with [console](https://github.com/fireball-packages/console) for display and query your logs
 - Global Selection
   - Selection cached and synced among windows
   - User can register his own selection type
   - Automatically filtering selections
 - Global Undo and Redo (Under Developing)
 - Enhance the native Dialog (Under Developing)
   - Remember dialog last edit position
 - Enhance Ipc Programming Experience
   - Add more Ipc methods to help sending and recieving ipc messages in different level
   - Allow sending ipc message to specific panel
   - Allow sending ipc message to specific window
   - Allow sending ipc request and waiting for the reply in callback function
   - Integrate with [ipc-debugger](https://github.com/fireball-packages/ipc-debugger) to help you writing better ipc code
 - An Auto-Test Workflow
   - Detect your package changes and automatically run tests under it in [tester](https://github.com/fireball-packages/tester)
   - Integrate [Mocha](mochajs.org), [Chai](http://chaijs.com/) and [Sinon](sinonjs.org) to our test framework
   - A ghost-tester to simulate UI events and behaviours for testing
   - Automatically recreate your test target (widgets, panels) after each test case

## License

MIT
