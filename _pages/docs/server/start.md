---
title: Server Start
permalink: /docs/server/start
toc: false
---

To start the server, run `/path/to/your/executable start`

This will run your server directly in the console. 
Normally you will wrap this command in an OS service configuration, but exactly how will depend on your flavor of Linux.  

To stop the service, `ctrl-c` or send it a SIGTERM signal. 
It may take a minute or two to shut down as it attempts to gracefully shut down all local containers.  
