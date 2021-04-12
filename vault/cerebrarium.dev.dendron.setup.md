---
id: 77b35550-fbbd-413c-9223-2d5b0a9df115
title: Setup
desc: ''
updated: 1614578559677
created: 1614578384156
---

# Setup

[build repo](https://dendron.so/notes/64f0e2d5-2c83-43df-9144-40f2c68935aa.html#3-build-repo)
    
- Do this every time you pull in from upstream
    ```sh
    npm install
    yarn bootstrap:bootstrap
    yarn bootstrap:build
    ```

- If something fails:
    ```sh
    ./bootstrap/scripts/cleanup.sh
    ```
    or fresh clone.

- Run this for continuous incremental build during development:
    ```sh
    ./bootstrap/scripts/watch.sh
    ```
