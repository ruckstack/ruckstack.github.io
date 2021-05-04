---
title: Ops Application
permalink: /docs/server/ops
---

## Overview

Your server includes an "Ops" application available at `/ops`. 

The job of ops is to provide a browser-based administration system for your application. 

<img src="/assets/images/status-page.png">

The base ops page is publicly available and includes a high-level status of the application plus the 
contact information you provided in your [project file](/docs/cli/project-file).

[Pro users](/pro) are provided with an option to log into the Ops application for more detailed information.

## Managing Ops Users (Pro Only)

The ops application maintains its own set of users using the server's `ops` command group

- /path/to/your/executable ops add-user
- /path/to/your/executable ops delete-user
- /path/to/your/executable ops list-users

Without a pro license installed in your builder, the server's CLI will have no `ops` command group.

## Ops Dashboard (Pro Only)

With a server build with a pro license, you are able to log into the ops dashboard using users created with the add-user command listed above.

The ops dashboard provides a more detailed breakdown of the health of the system, as well as links to the Kubernetes and Traefik dashboards

## Kubernetes Dashboard (Pro Only)

The standard Kubernetes dashboard provides an extensive view into the underlying Kubernetes system.

**WARNING:** the Kubernetes dashboard allows reconfiguration of the system, which provides both power and danger. Be careful of who you provide /ops access to.
{: .notice }

## Traefik Dashboard (Pro Only)

The standard traefik dashboard provides health metrics on the http routing system used in your server.

## Coming Soon (Pro Only)

In future releases, look for exciting expansions of the ops application!

Have suggestions on what to add? [Let us know](/community)
