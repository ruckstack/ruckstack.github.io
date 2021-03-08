---
title: Server Installation and Upgrade
permalink: /docs/server/install
---

The [build process](/docs/cli) will create an executable installer file.

Copy the installer to your server and execute it as root (usually through sudo).
The installer will prompt you for any needed install-time configuration values.

**Install Path** | Path to install your software to 
**Admin Group** | Existing OS group which will be given read/write/execute access to the installation files 
**Bind Address** | IP Address the server will bind to.
{: .flag-table}

#### System Requirements

- Linux OS (almost any flavor)
- 250M free RAM + whatever RAM your services require
- 500M free drive space + whatever drive space your services require
- Other dependencies: NONE 

## Upgrading

To upgrade the system, run `/path/to/your/executable upgrade --file /path/to/your-software.installer`.

## Uninstalling

The system can be uninstalled from a server with `/path/to/your/executable uninstall`. 

This will remove all software as well as reset any network changes made.   

