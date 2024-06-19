# gurukul-stage
This is repo for staging environment to test gurukul auto-update


package.json for stage :



{
  "name": "gurukul-stage",
  "version": "1.0.8",
  "description": "A client app",
  "main": "./src/main/main.js",
  "scripts": {
    "start": "electron .",
    "prepare": "husky install",
    "pack": "build --dir",
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "nodemon --exec electron .",
    "buildMAC": "npm i electron-builder@24.9.1 && electron-builder build --mac --publish never",
    "buildWIN": "npm i electron-builder@22.14.13 && electron-builder build --win --publish never",
    "deploy": "electron-builder build --mac --win --publish always"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/brightchamps-dev/gurukul-stage/"
  },
  "publish": {
    "provider": "github",
    "releaseType": "release"
  },
  "build": {
    "appId": "com.brightchamps.gurukul",
    "productName": "Brightchamps-Stage",
    "mac": {
      "target": [
        {
          "target": "default",
          "arch": [
            "x64",
            "arm64"
          ]
        }
      ],
      "darkModeSupport": true,
      "hardenedRuntime": true,
      "entitlements": "build-helpers/entitlements.mac.plist",
      "entitlementsInherit": "build-helpers/entitlements.mac.plist",
      "gatekeeperAssess": false,
      "category": "public.app-category.productivity",
      "extendInfo": {
        "NSCameraUsageDescription": "This app requires camera access for video calls",
        "NSMicrophoneUsageDescription": "This app requires microphone access for video calls",
        "com.apple.security.device.audio-input": true,
        "com.apple.security.device.camera": true
      },
      "icon": "build-helpers/images/icon.icns"
    },
    "dmg": {
      "icon": "build-helpers/images/icon.icns",
      "iconSize": 128
    },
    "nsis": {
      "oneClick": true,
      "perMachine": true,
      "allowToChangeInstallationDirectory": false,
      "deleteAppDataOnUninstall": true,
      "displayLanguageSelector": false,
      "shortcutName": "Brightchamps",
      "warningsAsErrors": true,
      "runAfterFinish": true,
      "createDesktopShortcut": "always",
      "createStartMenuShortcut": true,
      "menuCategory": false
    },
    "win": {
      "target": [
        {
          "target": "nsis",
          "arch": [
            "x64",
            "ia32"
          ]
        }
      ],
      "icon": "build-helpers/images/icon.ico"
    },
    "afterSign": "build-helpers/notarization.js",
    "directories": {
      "output": "dist"
    },
    "protocols": {
      "name": "gurukul-brightchamps",
      "schemes": [
        "gurukul-brightchamps"
      ]
    }
  },
  "author": "Brightchamps <developer.brightchamps.com>",
  "license": "ISC",
  "dependencies": {
    "@datastructures-js/priority-queue": "^6.3.1",
    "@nut-tree/nut-js": "^3.1.2",
    "axios": "1.6.7",
    "dotenv": "16.4.1",
    "electron-log": "^5.1.1",
    "electron-store": "^8.1.0",
    "electron-updater": "6.1.7",
    "husky": "9.0.7",
    "network-speed": "^2.1.1",
    "socket.io-client": "^4.7.4"
  },
  "devDependencies": {
    "electron": "^28.2.0",
    "electron-builder": "^22.14.13",
    "electron-notarize": "1.2.2",
    "eslint": "8.56.0",
    "nodemon": "3.0.3"
  }
}
