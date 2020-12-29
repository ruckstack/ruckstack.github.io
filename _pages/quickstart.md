---
title: Ruckstack Quick-Start Guide
permalink: /quickstart
---

1. [Download](/download) Ruckstack and extract it on your development and/or build machines
1. Run `ruckstack init --type=example` to generate a complete example project
1. Build your project with `ruckstack build`
1. Upload the `out/example-1.0.5.installer` file to a standard Linux server
1. On the linux server, run the `example-1.0.5.installer` file to install the application. Install it to /opt/example
1. Watch the services start up with `/opt/example/bin/example status`
1. Hit `http://SERVER_IP/` to see the running system 
c
