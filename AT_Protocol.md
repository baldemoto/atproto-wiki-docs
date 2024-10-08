---
title: AT Protocol
description: 
published: 1
date: 2024-10-08T22:20:16.250Z
tags: core protocol
editor: markdown
dateCreated: 2024-10-08T22:20:12.692Z
---

# What is the AT Protocol?
The **AT Protocol (Authenticated Transfer Protocol)**, also commonly abbreviated as **ATProto**, is an open communications protocol intended to be used for decentralized social networking services.

ATProto began as the "Authenticated Data Experiment" (ADX), a project within Twitter to explore the possibility of decentralizing the platform. The protocol was designed to adress various issues with other:

- **Platform interoperability** — Protocols such as ActivityPub run as separate, independent services which can choose to federate (share information) with each other. The choice to federate or defederate has led to fragmentation of services, with some users unable to see content posted by other users.
- **Discoverability** — Alternative decentralized protocols had no indexing mechanisms for the network. Because of this, discoverability-focused tooling, such as algorithmic feeds and user suggestions, were not possible at a protocol level
- **Network scalability** — Alternative decentralized protocols are composed of monolithic servers. These servers are responsible for storing user posts and data, tracking user follows, generating feeds, and fetching content from other federated servers. As such, a large influx of users can overload servers across the network.
- **User data and social graph portability** — Alternative decentralized protocols store user data in monolithic host servers. As such, protection against adversarial servers is next to impossible, and account migration often leads to a loss of user data, including user follows.

## [Core Protocol Components](/AT_Protocol/Core_Components):

The AT Protocol aims to solve these issues by splitting the services necessary for modern social media platforms into independently run microservices: Specifically, it splits up data storage, indexing, and social platforms into 3 core components:

### [**Personal Data Servers (PDSes)**](/AT_Protocol/Core_Components/Personal_Data_Server) 

**PDSes** store user data, posts, likes, etc. in [**Personal Data Repositories**](/AT_Protocol/Core_Components/Personal_Data_Server/Personal_Data_Repositories), commonly referred to as **repos**. PDSes serve as the access point for users, allowing users to add or remove [records](/AT_Protocol/Core_Components/Personal_Data_Server/Personal_Data_Repositories/Records) from their repos. They also serve repository updates to other network services.

### [**Relays**](/AT_Protocol/Core_Components/Relay)

**Relays** act as the core indexing mechanism for the protocol, crawling PDSes for repository updates, creating a repository of all network records, and forwarding repository updates to network services through federated network-wide data streams collectively termed the [**Firehose**](/AT_Protocol/Core_Components/Relay/Firehose).

### [**AppViews**](/AT_Protocol/Core_Components/AppView)

AppViews are end-user platforms and services which consume, process, and serve content from the Firehose to user clients. AppViews query user PDSes on the user's behalf, allowing users to update their repos and interact with content within the network.

## Opinionated Services

The protocol allows for integration of peripheal services for additional customization of the user's experience.

## User Identity