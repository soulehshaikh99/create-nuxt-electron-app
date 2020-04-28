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