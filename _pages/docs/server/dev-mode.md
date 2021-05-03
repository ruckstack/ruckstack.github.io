---
title: Dev Mode
permalink: /docs/server/dev-mode
---

## Overview

As your server moves its way through development and testing, there are features that are useful to enable to help with development and testing.

Your server's "Dev Mode" is disabled by default, but can be enabled to provide access to features useful during the creation and testing of your software.

**WARNING** Dev Mode is **NOT** intended for production systems and may impact performance and/or security.
{: .notice }

## Enabling Dev Mode

Dev mode is enabled by running `/path/to/your/executable dev enable`. 

Root access is required to enable dev mode.

## Disabling Dev Mode 

Once enabled, dev mode can be disabled by running `/path/to/your/executable dev disable`.

## Re-Routing Traffic

With dev mode enabled, you can re-route HTTP requests to external systems rather than the locally deployed service.

This allows you to run particular services in your standard development environments with all its debugging and reloading capabilities, 
while still allowing all the other services in your system to run and interact with it as normal.

### Reroute

The `dev reroute` command allows you to send all requests that normally would have gone to the given service
to an external host/port instead.

#### Available Flags

| \--service string | Service to replace (required) |
| \--target-host string | Host to proxy requests to (default "localhost") |
| \--target-port int | Port to proxy requests to (default 80) |
{: .flag-table}

### Remove Route

The `dev remove-route` command removes a previously configured service reroute.

#### Available Flags

| \--service string | Service to remove re-route |
{: .flag-table}

### Show Routes

The `dev show-routes` command shows all currently configured re-routes.

## More To Come

What else would help your development experience? [Let us know](/community)
