---
title: Ruckstack Builder
permalink: /docs/cli/
---

### Overview

Ruckstack combines all the pieces of your software stack into a single, customized installable system.

### Installing

To install Ruckstack, go to [the download page](/download) and choose the correct archive for your system.

After downloading, extract Ruckstack to your preferred directory.

### First Steps

Ruckstack uses a [ruckstack.conf project file](/docs/cli/project-config) to configure how it builds your application. 

You can create your ruckstack.conf file from scratch, or use the `ruckstack new-project --type <PROJECT_TYPE>` command to create starter files for you.

There are two types of projects to generate:

1. **"starter"** which is a mostly-bare but commented ruckstack.conf file
1. **"example"** which is a complete and buildable example project    

### Configuring Your Project

Open your ruckstack.conf file in your favorite text editor to configure your project.

In the config file, you will set the information Ruckstack needs to brand and personalize your server as well as configure your services.

For more information on how to configure your project, see the [project config documentation](/docs/cli/project-config).

### Building Your Project

Once you have configured your project, build it with `ruckstack build --project /path/to/ruckstack.conf --out /path/to/out/dir`.

The build command will package your stack into an installable server which you can run on any Linux system.

For more information on installing and using the server, see the [server documentation](/docs/server/).

