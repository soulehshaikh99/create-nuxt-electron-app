<div align="center">
<img alt="Electron Vue" src="https://raw.githubusercontent.com/soulehshaikh99/repo/master/svg/Electron_Nuxt.svg" width="550" />
</div>
<br />
<div align="center">

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://forthebadge.com)&nbsp;&nbsp;&nbsp;&nbsp;[![forthebadge](http://forthebadge.com/images/badges/makes-people-smile.svg)](http://forthebadge.com)<br />

[![forthebadge](http://forthebadge.com/images/badges/uses-html.svg)](http://forthebadge.com)&nbsp;&nbsp;&nbsp;[![forthebadge](http://forthebadge.com/images/badges/uses-css.svg)](http://forthebadge.com)&nbsp;&nbsp;&nbsp;[![forthebadge](http://forthebadge.com/images/badges/uses-js.svg)](http://forthebadge.com)

</div>

## ✒️ Overview

The aim of this project is to provide Web Developers using `nuxt.js` the power to create cross-platform desktop apps using `electron`. 

#### 🧐 What packages does the project use?
**`electron`** enables you to create desktop applications with pure JavaScript by providing a runtime with rich native (operating system) APIs. You could see it as a variant of the Node.js runtime that is focused on desktop applications instead of web servers.

**`electron-builder`** is used as a complete solution to package and build a ready for distribution (supports Numerous target formats) Electron app with "auto update" support out of the box.

**`electron-serve`** is used for Static file serving for Electron apps.

**`nuxt`** is the Progressive Vue.js Framework which lets you build your next Vue.js application with confidence using NuxtJS. An open source framework making web development simple and powerful. Nuxt.js can produce Universal, Single Page and Static Generated Applications.

**`concurrently`** is used to run multiple commands concurrently.

**`wait-on`** is used as it can wait for sockets, and http(s) resources to become available.

## 🚀 Getting Started

**Note:** If you wish to use npm over yarn then modify package.json by replacing `yarn` with `npm` in `electron-dev` and `preelectron-pack` scripts.
But I strongly recommend using <em>yarn</em> as it is a better choice when compared to <em>npm</em>.

### 🤓 Use this boilerplate

```bash
# Clone the Project
# GitHub CLI Users
$ gh repo clone https://github.com/soulehshaikh99/create-nuxt-electron-app.git
# or Normal Git Users
$ git clone https://github.com/soulehshaikh99/create-nuxt-electron-app.git

# Switch location to the cloned directory
$ cd create-nuxt-electron-app

# Install dependencies
$ yarn # or npm install

# Run your app
$ yarn electron-dev # or npm run electron-dev

# Package Your App
$ yarn electron-pack # or npm run electron-pack
```

### 💫 Create this boilerplate from scratch (Manual Setup)

#### 1) Download the app icon

[favicon.png](https://raw.githubusercontent.com/soulehshaikh99/create-nuxt-electron-app/master/static/favicon.png)


#### 2) Create a nuxt.js project using scaffolding tool create-nuxt-app.
```bash
$ yarn create nuxt-app create-nuxt-electron-app
# npx create-nuxt-app create-nuxt-electron-app
```

#### 3) Change Directory
```bash
$ cd create-nuxt-electron-app
```

#### 4) Move all dependencies to devDependencies using IDE / Text Editor

```bash
# You might have more dependencies than this, but put all of them
# inside devDependencies as thay are not needed once the app is packaged. 
"dependencies": {},
"devDependencies": {
  "nuxt": "^2.0.0"
}
```

#### 5) Install Development Dependencies
```bash
$ yarn add --dev electron electron-builder wait-on concurrently
# npm i -D electron electron-builder wait-on concurrently
```

#### 6) Install Production Dependency
```bash
$ yarn add electron-serve # or npm i electron-serve
```

#### 7) Your dependencies might look like this

```json
"dependencies": {
  "electron-serve": "^1.0.0"
},
"devDependencies": {
  "concurrently": "^5.2.0",
  "electron": "^8.2.3",
  "electron-builder": "^22.5.1",
  "nuxt": "^2.0.0",
  "wait-on": "^4.0.2"
}
```

#### 8) Create main.js file (serves as entry point for Electron App's Main Process)
```bash
$ notepad.exe main.js # Windows Users
$ touch main.js # Linux and macOS Users
```

#### 9) Paste the below code in main.js file
```js
// Modules to control application life and create native browser window
const { app, BrowserWindow } = require('electron');
const path = require('path');
const serve = require('electron-serve');
const loadURL = serve({ directory: 'build' });

// Keep a global reference of the window object, if you don't, the window will
// be closed automatically when the JavaScript object is garbage collected.
let mainWindow;

function isDev() {
    return !app.isPackaged;
}

function createWindow() {
    // Create the browser window.
    mainWindow = new BrowserWindow({
        width: 800,
        height: 600,
        webPreferences: {
            nodeIntegration: true
        },
        // Use this in development mode.
        icon: isDev() ? path.join(process.cwd(), 'static/favicon.png') : path.join(__dirname, 'build/favicon.png'),
        // Use this in production mode.
        // icon: path.join(__dirname, 'build/favicon.png'),
        show: false
    });

    // This block of code is intended for development purpose only.
    // Delete this entire block of code when you are ready to package the application.
    if (isDev()) {
        mainWindow.loadURL('http://localhost:3000/');
    } else {
        //Do not delete this statement, Use this piece of code when packaging app for production environment
        loadURL(mainWindow);
    }
    
    // Uncomment the following line of code when app is ready to be packaged.
    // loadURL(mainWindow);

    // Open the DevTools and also disable Electron Security Warning.
    // process.env['ELECTRON_DISABLE_SECURITY_WARNINGS'] = true;
    // mainWindow.webContents.openDevTools();

    // Emitted when the window is closed.
    mainWindow.on('closed', function () {
        // Dereference the window object, usually you would store windows
        // in an array if your app supports multi windows, this is the time
        // when you should delete the corresponding element.
        mainWindow = null
    });

    // Emitted when the window is ready to be shown
    // This helps in showing the window gracefully.
    mainWindow.once('ready-to-show', () => {
        mainWindow.show()
    });
}

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.on('ready', createWindow);

// Quit when all windows are closed.
app.on('window-all-closed', function () {
    // On macOS it is common for applications and their menu bar
    // to stay active until the user quits explicitly with Cmd + Q
    if (process.platform !== 'darwin') app.quit()
});

app.on('activate', function () {
    // On macOS it's common to re-create a window in the app when the
    // dock icon is clicked and there are no other windows open.
    if (mainWindow === null) createWindow()
});

// In this file you can include the rest of your app's specific main process
// code. You can also put them in separate files and require them here.
```

#### 10) Add electron, electron-dev, preelectron-pack and electron-pack scripts

```bash
# Add this scripts
"electron": "wait-on http://localhost:3000 && electron .",
"electron-dev": "concurrently \"yarn dev\" \"yarn electron\"",
"preelectron-pack": "yarn generate",
"electron-pack": "electron-builder"

# You should end up with something similar
"scripts": {
  "dev": "nuxt",
  "build": "nuxt build",
  "start": "nuxt start",
  "generate": "nuxt generate",
  "electron": "wait-on http://localhost:3000 && electron .",
  "electron-dev": "concurrently \"yarn dev\" \"yarn electron\"",
  "preelectron-pack": "yarn generate",
  "electron-pack": "electron-builder"
}
```
#### 11) Add the following Electron Configuration in package.json
**Note:** build configuration is used by electron-builder, modify it if you wish to add more packaging and native distribution options for different OS Platforms.
```json
"main": "main.js",
"build": {
  "icon": "static/favicon.png",
  "productName": "Nuxt and Electron App",
  "files": [
    "build/**/*",
    "!build/favicon.png",
    "main.js"
  ]
}
```

#### 12) Test drive your app
```bash
# Run your app
$ yarn electron-dev # or npm run electron-dev

# Package Your App
$ yarn electron-pack # or npm run electron-pack
```

<h3>😍 Made with ❤️ from Souleh</h3>

[![forthebadge](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)
<br/>
<h3>📋 License: </h3>
Licensed under the <a href="https://github.com/soulehshaikh99/create-nuxt-electron-app/blob/master/LICENSE">MIT License</a>.