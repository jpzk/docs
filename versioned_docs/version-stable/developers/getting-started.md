---
sidebar_label: Getting started
description: "Overview of areas of potential development."
hide_title: false
title: "Getting started" 
---

If you are a coder, we invite you to build privacy enhanced applications - **PEAPs** - using Nym.

## Where to start?
Nym's infrastructure is complex, and might be a little overwhelming when you just want to build your 'hello world' app when getting started. In order to assess what to build (and which area to build it on) use the general rule of thumb that:
* Nym apps focus on anonymising _network-level_ communications by using privacy respecting clients and services to send data through the mixnet, and stop metadata leakage: think anonymous chat applications, or services which proxy a cryptocurrency transaction for you and prevent metadata leaks deanonymising you when broadcasting your tx. 
* Nyx apps focus more on the _application_ level, involving smart contracts hosted on the Nyx chain, and/or anonymous, reusable Coconut Credentials for anonymous access control. 

The list above isn't exhaustive, nor does it necessarily imagine that apps won't utilise Nym's technologies to provide anonymity at both the network and application levels, but it provides a rough direction in which to start when researching building something atop Nym. 

If you're still looking for that 'hello world' app, guides and example applications will be coming soon.  

## What to build?
Once you've decided which part of the stack best serves your aims, you have to decide what to build. There are various options listed below to get started with.

### Example Nym (Mixnet) PEAPs
* Chat applications 
* Crypto RPC requesters (think our [Network Requester](/docs/stable/run-nym-nodes/nodes/requester), but for blockchain transactions)
* Private file storage (see the winner and runners up from the previous Hackatom [here](/docs/stable/run-nym-nodes/nodes/file-storage), who built just this)
* Mail server requesters (anonymously access mailboxes)
* Private file backups 

### Example Nyx (smart contract) PEAPs
* Privacy-preserving Covid Passport (you can find a POC of this in our [Github repo](https://github.com/orgs/nymtech/repositories?type=all))
* Privacy-preserving KYC
* Replacements for DID systems
* Cryptocurrencies 
* Anything that requires access control that you wish to anonymise!

### Hack on Nym infrastructure 
If you're wanting to develop on top of the infrastructure code itself and start adding additional features to existing nodes, check out the [Nym github repository](https://github.com/nymtech/nym). If you want to get to grips with running a node before starting this, check out the [Node Operators](/docs/stable/run-nym-nodes/pre-built-binaries) section of these docs for more.  

## Integrations with existing apps 
If you're building an application that you think could benefit from utilising the Nym network, get in touch via [max@nymtech.net](mailto:max@nymtech.net) or via [Discord](Discord.gg/nym) or Keybase (search for the `nymtech.friends` teams).  
