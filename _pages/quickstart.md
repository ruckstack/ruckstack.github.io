---
title: Ruckstack Quick-Start Guide
layout: single
permalink: /quickstart
sidebar:
    nav: "docs"
---

1. [Download](/download) Ruckstack and install it on your development machine
1. Run `ruckstack new-project --type=example` to generate a complete example project
1. Build your project with `ruckstack build --project ruckstack.project.config`
1. Upload the `out/example-1.0.5-installer.run` file to a standard Linux server
1. On the linux server, run the `example-1.0.5-installer.run` file to install the application. Install it to /opt/example
1. Watch the services start up with `/opt/example/bin/example status`
1. Hit `http://SERVER_IP/` to see the running system 