---
title: "About"
description: "About ForgeFlux - A project that is involved in software forgefederation"
date: 2022-07-13
lastmod: 2022-07-13 11:58
draft: false
images: []
---

ForgeFlux is an attempt at implementing
[ForgeFed](https://forgefed.peers.community")
external to
[Forges](<href="https://en.wikipedia.org/wiki/Forge_(software)>)
to provide a decentralised development environment. If successful, major
software development workflows like pull requests/patches and bug
trackers will be available in a decentralised context.

## Why

Free software developers are asked to choose between freedom and having
access to a large community while choosing a
[software forge](<https://en.wikipedia.org/wiki/Forge_(software)>)
Some are willing to make compromises to their freedom in the hopes of
developing a community around their project while others don't. Either
way, these are compromises.

Additionally, participating in Free Software projects require creating
and configuring accounts on the forge instances that the projects use.
Maintaining multiple accounts is a time-consuming process.

A mechanism to enable developers on independently run forge instances to
interact with other forge instances using a single account would solve
the issues that mentioned above.
[ForgeFed](https://forgefed.peers.community/") is an attempt
to do just that. But implementing native support for ForgeFed will
require changes to the forge's source code, which we find to be a
time-consuming process.

ForgeFlux will implement ForgeFed external to the forges, using the
forge's HTTP APIs. Officially, external federation for Gitea, SourceHut,
GitLab and GitHub will be implemented but the project will also provide
tools and guidelines to implement federation for unsupported forges.

## How?

ForgeFlux will act as an adaptor that will enable federation on forge
instances by running alongside the forge instances. The deployment
architecture is very similar to how a third-party integration like
[Woodpecker CI](https://woodpecker-ci.org/) works with
[Gitea](https://gitea.com) deploy ForgeFlux next to a
forge instance and configure authentication to enable federation on the
forge instance.

ForgeFlux software is made-up of multiple components, each of which
makes up for the lack of native federation features in supported forges:

## Components

### Interface: Federation Adaptor

Interface uses data received from Forge APIs to provide an interface
that supports ForgeFed. It includes tools and mechanisms to
implement support for forges that are not Officially supported by
ForgeFlux.

### Northstar: Forge-Interface Discovery service</h3>

ForgeFlux allows for multiple interfaces to be run against a single
software forge. Also, the protocol is flexible enough to support
multiple types of software forges(GitLab, GitHub, etc). The
protocol's decentralised nature makes it impossible to create a
reliable record of which interfaces service which forges.

So we created a discovery service which stores records of interfaces
and the forges they service. This is very similar to the way DNS
works. In DNS, hostname is resolved to IP address. Here, software
forge URL is resolved to URLs of interfaces that service the queried
forge.

### Starchart: Federated Repository Explorer</h3>

Forges provide means for exploring projects that are hosted on the
forge instance. The federated forge ecosystem needs something
similar. Starchart solves this problem by crawling the federated
forge ecosystem(the forge admins will have to authorize crawling)
and publishing the data for for indexing by search engines and also
by providing a centralized service to people to explore projects on
the federated ecosystem.
