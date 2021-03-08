---
title: Ruckstack Builder
permalink: /docs/cli/
---

## Overview

Ruckstack combines all the pieces of your software stack into a single, customized installable system.

## Installing

To install Ruckstack, go to [the download page](/download) and choose the correct executable for your system.

## System Requirements
Builder Requirements:
- [Docker Engine 18.09+ OR Docker Desktop 2.1+](https://docker.io)
  - Used for building the service images

## First Steps

Ruckstack uses a [ruckstack.yaml project file](/docs/cli/project-file) to configure how it builds your application. 

You can create your ruckstack.yaml file from scratch, or use the `ruckstack init --type <PROJECT_TYPE>` command to create starter files for you.

There are two types of projects to generate:

1. **"empty"** which is a mostly-bare but commented ruckstack.yaml file
1. **"example"** which is a complete and buildable example project    

## Configuring Your Project

Open your ruckstack.yaml file in your favorite text editor to configure your project.

In the config file, you will set the information Ruckstack needs to brand and personalize your server as well as configure your services.

For more information on how to configure your project, see the [project file documentation](/docs/cli/project-file).

## Building Your Project

Once you have configured your project, build it with `ruckstack build`.

The build command will package your stack into an installable server which you can run on any Linux system.

For more information on installing and using the server, see the [server documentation](/docs/server/).

