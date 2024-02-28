---
title: Development Assets
ShowShareButtons: false
hideMeta: true
tags: ["Tips", "Xcode"]
---

The default Xcode template contains a **Preview Content** folder, ideal for placing assets only used in previews and mocking data for tests.

This works thanks to `DEVELOPMENT_ASSET_PATHS` ([reference](https://developer.apple.com/documentation/xcode/build-settings-reference#Development-Assets)), a build setting defining files and directories _excluded from archive and install builds_.
