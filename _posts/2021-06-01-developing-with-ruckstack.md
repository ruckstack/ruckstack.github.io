---
title:  "Developing With Ruckstack"
excerpt: "Use 'dev reroute' to keep your iteration cycle fast"
---

Packaging your software with Ruckstack doesn't mean you have to lose the development tools you are used to. 

In fact, Ruckstack can simplify and streamline your development environment by letting you focus on developing the specific
pieces of your application you are currently interested in, while letting the rest run as they always do.

Let's start with a typical application like the sample one you get with `ruckstack init --template example`. 
It includes an HTML frontend, a backend written in NodeJS, and a PostgreSQL database. You can see the configuration in detail by looking at the generated `ruckstack.yaml` file.

Running `ruckstack build` is great for building a distributable artifact, 
but when you are actively building on your software you need debugging, hot swapping, and everything else you need to be productive.

That is where "Re-Routing" comes in.

### What Is Re-Routing?

One of the features of [dev mode](/docs/server/dev-mode) is the ability to configure your Ruckstack-packaged system
to route requests to an external server instead of the packaged version.

This allows you to serve specific HTTP requests not from an isolated/packaged system, but from a server running in your favorite development environment.

Because that re-route happens transparently to all the other services, the rest of your application continues to function correctly.  

### Enabling Dev Mode

After installing a Ruckstack-packaged version of your application (perhaps from your build server), run `example-manager dev enable` as root to switch it into "Dev Mode".

```
bash$ sudo bin/example-manager dev enable
WARNING: 'Development Mode' is designed to help with the development and testing of this system.
WARNING: It is NOT intended for production systems and may impact performance and/or security.

Enable Development Mode: [y|N]
y
Development mode enabled
```

NOTE: If you have already enabled dev mode on your system, you can skip this step.

### Rerouting Services

Now that dev mode is enabled, we can leverage the "reroute" functionality to help us work on the backend code.

With your packaged server up and running on your machine, hitting `http://localhost` will bring up the "Welcome to Ruckstack" page. Try it quick -- just to make sure.

Now run `example-manager dev reroute` to reroute all requests that would have gone to the packaged backend service to go to `localhost:8080` instead.

```
bash$ bin/example-manager dev reroute --service backend --target-host localhost --target-port 8080
Requests for service 'backend' will now be proxied to http://localhost:8080
```

Now, when you go back to `http://localhost`, you get a popup saying `Error reading notes: Gateway Timeout`. That is what you want, because it is telling you the server is trying to proxy to `localhost:8080` but cannot connect because we have not started that server yet. 

### Starting Your Local Backend Server

In your project directory, we need to configure and start the backend service locally.

Often, you will have configuration files to set up your local server instances. 
In our case, we have `POSTGRES_HOST` and `POSTGRES_PASSWORD` environment variables which can be used to control the database
to connect to.

Because we have the packaged PostgreSQL's port configured to be accessible, our local backend server
can talk directly to that packaged database. The database's password is randomly generated on install, but it can be found with `example-manager secure-config-data show`

```
bash$ cd backend
bash$ export POSTGRES_HOST=<CONFIGURED EXTERNAL IP>
bash$ export POSTGRES_PASSWORD="$(sudo bin/example-manager secure-config-data show --name postgresql --key postgresql-password)"
bash$ npm install
```

You will also normally want to run your service with `nodaemon` or something similar to help with reloading and debugging. 
For simplicity, we are simply running it directly.

```
bash$ nodejs server.js
Running on http://0.0.0.0:8080
Notes table created
```

Now, when you hit `http://localhost` the app loads like normal -- **but the packaged frontend service is actually talking to your separately running backend server**. You can see that because your local service logs `Requested GET /api/notes`. 

With your backend running as you want for development, quickly iterate your changes without needing to do the entire Ruckstack packing cycle for each change.

### Back To Normal

When you are done working on your backend service, run `example-manager dev remove-route` to remove the route and serve the packaged backend service as normal.

```
bash$ bin/example-manager dev remove-route --service backend
Requests for service 'backend' will now be served by the packaged service.
```

### Summary

The example Ruckstack project uses a NodeJS service, but the same pattern applies to any technology you use:  

1. Start your Ruckstack-packaged system as normal
1. Start the service you are developing in whatever tooling you prefer
1. Reroute requests in your packaged system to be handled by your in-development server
1. Profit!
