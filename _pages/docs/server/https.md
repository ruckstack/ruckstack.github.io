---
title: HTTPS/SSL Management 
permalink: /docs/server/https 
---

By default, your server runs without https support. Often times, the https connection is managed in a load balancer, but
it can be enabled directly in the server as well.

## Obtaining a Signed Certificate

The first thing that needs to be done is to generate a private key and certificate, signed by a trusted certificate
authority.

Customers will often have their own systems in place for generating keys and signing them. The installed server simply
needs a private key file, and a signed certificate in PEM format. Those files can be created in whatever way works best.

### Generating a Self-Signed certificate

One option for starting the certificate process is to use `/path/to/your/executable https generate-key`.

This will create:

1. A private key
1. A self-signed certificate
1. A certificate signing request

**NOTE:** Because browsers warn against self-signed certificates, you will normally want to get the certificate signed before importing it.
{: .notice }

#### Available Flags

| \--output string | Directory to save files in. Defaults to current directory |
{: .flag-table}

## Importing the Key

No matter how you create your key and certificate, it can be imported with `/path/to/your/executable https import`.

Importing the key and certificate will automatically enable and require https connections, but the server **must be manually restarted** for the https
support to be enabled.

#### Available Flags

| \--certificate string | File containing the certificate |
| \--private-key string | File containing the private key |
{: .flag-table}
