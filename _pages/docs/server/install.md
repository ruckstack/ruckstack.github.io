---
title: Server Installation and Upgrade
permalink: /docs/server/install
layout: single
sidebar:
    nav: "docs"
---

The [build process](/docs/cli) will create a "run" file which is an executable installer.

Copy the installer to your server and execute it as root (usually through sudo).
The installer will prompt you for any needed install-time configuration values.

**Install Path** | Path to install your software to 
**Admin Group** | Existing OS group which will be given read/write/execute access to the installation files 
**Bind Address** | IP Address the server will bind to. 
  
#### System Requirements

- Linux OS (almost any flavor)
- 250M free RAM + whatever RAM your services require
- 500M free drive space + whatever drive space your services require
- Other dependencies: NONE 

## Upgrading

To upgrade the system, run `system-control upgrade --file /path/to/installer.run`.

## Uninstalling

The system can be uninstalled from a server with `system-control uninstall`. 

This will remove all software as well as reset any network changes made.   

