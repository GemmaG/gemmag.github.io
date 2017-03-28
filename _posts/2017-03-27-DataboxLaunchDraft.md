---
title: Databox Open-Source Software Community Launch
layout: post
author: gemmag
category: Events
tags: mirage databox platform opensource events community outreach conference
---

The team working on the [Databox Project](http://www.databoxproject.uk/) hosted their Cambridge open-source community launch on Friday 24th March at [Darwin College](https://www.darwin.cam.ac.uk/), Cambridge.

The event served to introduce the motives behind Databox, the structure of the project and to gauge use cases within the community and potential application developers. The team presented the initial release of a working open source Databox platform, which includes basic data collection support through mobile sensing libraries and selected APIs, provides basic data flow policing and privacy policy enforcement, and supports installation and operation of simple personal data processing apps.

<p>
<img src="/images/databox.jpg" alt="Stage 1" width="200" />
<img src="/images/databox2.jpg" alt="Stage 1" width="200" />
<img src="/images/databox3.jpg" alt="Stage 1" width="200" />
</p>

_Photos courtesy of [Hamed Haddadi](https://twitter.com/realhamed)._

**"Can we do detailed, user-centric, contextual analytics at a scalable rate without privacy disasters and legal challenges?"**

The morning session began with a formal introduction by [Hamed Haddadi](https://twitter.com/realhamed) into the research project itself, explaining the high-level goals of the project: "Can we do detailed, user-centric, contextual analytics at a scalable rate without privacy disasters and legal challenges?" [Richard Mortier](https://github.com/mor1) followed with a summary of the technical architecture of the Databox and described the driving motive as an open-source, personal networked system, **NOT** another data silo that acts as a honey pot - the focus being to move computation to where the data is, thus reducing the movement of data itself. [Tosh Brown](https://github.com/Toshbrown) and [Yousef Amar](https://github.com/yousefamar) then followed with (working!) demonstrations of the Databox SDK and UI, and development of drivers and applications at the container level.

The afternoon session was driven by the attendees, who were all asked to propose applications for and uses of the Databox, with small focus groups facilitating this development.

**Contribute to the open-source software Databox project**

You can contribute to the open-source Databox prototype by visiting the [repository](https://github.com/me-box) and checking out the [code](https://github.com/me-box/databox) and [docs](https://github.com/me-box/documents).

View [application](https://github.com/me-box/databox-app-template-node) and [driver](https://github.com/me-box/databox-driver-template-node) templates in the GitHub repository to get started.

See my raw notes from the event below.

Thank you to all those who attended, the Databox Project team, and to the staff at Darwin College.

----

## Motivations

The Databox seeks to collate, curate and mediate third-party access to your personal data, whilst creating a user-friendly environment to effectively manage your data. We are generating data more than ever in the form of wearables, social media etc, and our digital footprint can be used by third parties to infer a wealth of information about us. Currently the user has little choice about which data is shared and with whom it is shared - we need a privacy-aware data analytics platform.

## Technical Architecture and Design Principles

Performing local data processing and moving data as little as possible has benefits including:

- context retention
- reduction of honey pot effects
- efficiency, and latency reduction
- more varied sources of accessible data: Twitter, home IoT devices, smartphone sensing etc

### Design principles:

- clear separation of components
  - intercommunication via specified applications
  - use of containers e.g. docker
- distinct data sources represented by distinct data stores - if one is leaked, only that data is exposed, not all data
- components are disconnected by default - reduces the attack surface - containers cannot talk to arbitrary cloud services - they will have to go through an export service
- data flow logged for audit - log store for audit with tools to process logging information
  - how is data being used and moved/exported
  - data processing is transparent to users to allow better control and understanding

Platform components that form the core:

- container manager: managing apps, starting/stopping containers - UI/dashboard
- log store (separate container currently) to log all actions
- arbiter: minting tokens, permissions (separate container atm), root level catalogue uses hypercat with nested catalogues
- export service: data is taken off the box and sent elsewhere - specific set of requirements meaning that no data can leave the box without being permitted to do so by the user

Dynamic components that you may install to interact with services and data:

- drivers - interact with services e.g. Hue, Twitter - drivers are containers. Interaction via RestAPI with a data store attached for those logs
- apps process the data, where the computation is. Apps installed as containers with explicit permissions upon installation and provided by the arbiter to allow them to access specific data.

## UI and SDK

The [SDK](https://sdk.iotdatabox.com/login) provides a user-friendly cloud environment for building Databox applications quickly, and finding approved applications to use on your own Databox - you simply require a GitHub login to access it. The graphical programming environment allows you drag in and connect nodes, view the function output, and debug if needed. There are other useful details such as built-in virtualisations that allow you to view your data as graphs, lists etc, and application manifests which include any resources your app needs and different levels of functionality to correspond with existing devices. Current applications include Hue lights, a mobile sensing driver and Twitter.

<p>
<img src="/images/DataboxSDK.png" alt="Stage 1" width="200" />
</p>

## Apps and Drivers

In the Databox, an application can talk interact with 3 areas:

- stores (both data and driver)
- arbiter
- export service

An application includes:

- app manifests: description, resources required, metadata, textual representation of permissions that the app might request, standard dockerfile (+ databox label, and UI port exposure details) to build app
- environment variables: urls for containers to connect to, data source metadata in [Hypercat](http://www.hypercat.io/) format, url for data source store, CA root certificate for the container for use over https (and a private key if you want to host on https server)
