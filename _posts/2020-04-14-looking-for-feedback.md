---
title:  "Looking for Feedback"
excerpt: "While there is still a lot to do, all the major concepts should be there enough to start talking about and experimenting with."
---

Now that [Ruckstack 0.7.0](blog/2020/04/ruckstack-0.7.0-released) is out, I'm looking for feedback and help.

While there is still a lot to do, all the major concepts should be there enough to start talking about and experimenting with.

## What is Ruckstack?

Ruckstack is an attempt to build a better application server for independent software vendors (ISVs). 

* Deploying your application into other people's environments is hard--so many different OS and network configurations to deal with. 
* Your customers need your application to be always available, but you don't have easy access to their systems and they don't have the troubleshooting and management knowledge you have.  
* You want to use on external services and components, but every additional process and system increases your installation complexity.

<img src="/assets/images/blog/no-cloud.jpg" align="left" style="margin-right: 20px">

Ruckstack solves these problems by leveraging container and Kubernetes technologies--but scaled to application-size NOT datacenter-size.        

For more details on what Ruckstack does, [see the docs](/docs)

## The Big Question: Does the Idea Even Make Sense?

The cloud is the future -- is this even a problem to solve in 2020???

There are all sorts of great cloud-native tools for installing, managing, and monitoring services. 
AWS, Azure, and friends all have nice marketplaces of services to install, with auto-provisioning and cloud-watch options.

But, as an ISV I see three major problems to deal with:

1. **Not all software can be installed in the cloud.** Some applications contain information that can't be safely stored there. Some applications need access to local-network resources. 
1. **Every cloud provider's tooling is unique.** If you were creating in-house software, building your software around AWS's infrastructure is great. But, if you are creating software to sell to thousands of customers, you have to support ALL the cloud providers lose sales. That is NOT great.
1. **The cloud is not as ubiquitous as it seems.** Despite all the hype and push, cloud usage is far from 100%. Many customers still rely on traditional datacenters today. Many are foregoing the public cloud and building their own, in-house infrastructure. Many are in the middle of a multi-year transition.

**As an ISV, you can't be losing deals because your software isn't compatible with existing environments.**

<img src="/assets/images/blog/change-mind.jpg" align="right" style="margin-left: 20px">

My belief is that ISVs need the functional and power of "cloud" technologies, but cannot stake their business on that infrastructure being available. 

They need a way to provide the "turn-key" installation customers expect, while taking advantage of the capabilities that cloud-native apps enjoy.

## Looking For Help

**The #1 thing I need right now, is an answer to "Does This Even Make Sense?"** 

Email me at [ruckstack@hour23.com](mailto:ruckstack@hour23.com) or message [@ruckstack on twitter](https://twitter.com/ruckstack) with your thoughts.

If you think it's not needed, let me know so I don't waste my time. I've ran open source projects before--criticism doesn't phase me.  
      
If you feel like you would potentially find it useful, make sure to let me know. I'm doing this as an open source project--knowing I'm helping others is the major driving force.

**How can the docs be better?**

What confuses you about what [ruckstack.org](/) is saying? What is unclear? What is wrong? What is missing? 

I've been building Ruckstack for a while now, so it's hard to see it from fresh eyes. Please be those fresh eyes for me.

**What more can it do?**

I know the features **I** need for the software I've built over the years, but what do **YOU** need? I know you have great ideas I've never though of.

Log them in the [issue tracker](https://github.com/ruckstack/ruckstack/issues) or [email me](mailto:ruckstack@hour23.com) them.

**I'm always open to pull requests**

In the end, Ruckstack is glue between a bunch of other successful open source projects. But it is a lot of glue. 
I appreciate any, and all development help. Just send a pull request on [Github](https://github.com/ruckstack/ruckstack)                      
