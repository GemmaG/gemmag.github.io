---
title: Databox Open-Source Software Community Launch
layout: post
author: gemmag
category: Events
tags: mirage databox platform opensource events community outreach conference
---

The team working on the [Databox Project](http://www.databoxproject.uk/) hosted their Cambridge open-source community launch on Friday 24th March at Darwin College, Cambridge.

The event served to introduce the motives behind Databox, the structure of the project and to gauge use cases within the community and potential application developers. The team presented the initial release of a working open source Databox platform, which can be run on any device capable of running Docker containers. This initial release includes basic data collection support through mobile sensing libraries and selected APIs, provides basic data flow policing and privacy policy enforcement, and supports installation and operation of simple personal data processing apps.

<p>
<img src="/images/databox.jpg" alt="Stage 1" width="200" />
</p>

The morning session began with a formal introduction by [Hamed Haddadi](https://twitter.com/realhamed) into the research project itself, explaining the high-level goals of the project: "Can we do detailed, user-centric, contextual analytics at a scalable rate without privacy disasters and legal challenges?" [Richard Mortier](https://github.com/mor1) followed with a summary of the technical architecture of the Databox and described the driving motive as an open-source, personal networked system, NOT another data silo that acts as a honey pot - the focus being to move computation to where the data is, thus reducing the movement of data itself. [Tosh Brown](https://github.com/Toshbrown) and [Yousef Amar](https://github.com/yousefamar) then followed with (working!) demonstrations of the Databox SDK and UI, and development of drivers and applications at the container level.

The afternoon session was driven by the attendees, who were all asked to propose applications for and uses of the Databox, with small focus groups facilitating this development.

You can contribute to the open-source Databox prototype by visiting the [repository](https://github.com/me-box) and checking out the [code](https://github.com/me-box/databox) and [docs](https://github.com/me-box/documents).

See my raw notes from the event below.

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
- environment variables: urls for containers to connect to, data source metadata in hypercat format, url for data source store, CA root certificate for the container for use over https (and a private key if you want to host on https server)

You can view [application](https://github.com/me-box/databox-app-template-node) and [driver](https://github.com/me-box/databox-driver-template-node) templates in the GitHub repository to get started.






-----
-----


lower level development at the container level

app can talk to:
- stores (data and driver)
- arbiter
- export service

What makes an app?

app manifests: description, resources required, metadata, textual representation of permissions that the app might request, standard dockerfile (+ databox label, and UI port exposure details) to build app

environment variables: urls for containers to connect to, data source metadata in hypercat format, url for data source store, CA root certificate for the container for use over https (and a private key if you want to host on https server)

docker 1.13 - not passing secrets via environment variables. What about versioning the revision of the metadata? Currently just a repo of specs - would be good to add versioning. Repo to report issues:

overview:
- https communication
- rest apis
- direct mapping of http methods to crud functions
- pre-route granular permissions
- network-level isolation
- content security policy (CSP) to sandbox UIs

requesting tokens:
- SLA process updates arbiter wrt to permissions for that app
- arbiter checks these and will issue a token

reading/writing to/from stores
- websocket subscription events - for new data
- endpoints

dev workflow
- install docker and git
- clone databox
- launch in dev mode
- create dockerfile and manifest
- upload manifest to local manifest server
- build docker image and push to local registry
- browse to dashboard interface and launch

launch app as staging container....

exporting:
logs any requests on a small server run in the cloud - data export destination

----

driver manifest is simpler than an app manifest as it doesn't need to specify the data sources

environment variables - link to the datastore present in the manifest

----

components built so far
process by which you can build some

-----

Databox

mobile
home
cloud

not bound by home connectivity
phd student working on a personal vpn service - provides data and connectivity and capture data from all of your devices connected to that vpn - covers mobility issues

qi - export service


----

----

databox technical architecture

not moving data around, moving computation instead - move the computation to where the data is, and move data as little as possible
- loss of context
- legal issues and ethical considerations

more local processing where the data is generated

benefits:
- reducing honeypot effects
- process data locally -> privacy, efficiency, latency, minimise data export
- eg. sentiment analysis on all communications - more sources of data accessible than other
      household occupancy via face detection on front-door video feed - reducing bandwidth

implementing HDI
data processors ask for permission to access your data - allow them to use your databox to do computation on your data and then return the results - a server that can receive computed values - support for a distributed system rather than all in one place.

physical data box will allow interactions not possible on the cloud - e.g certain exported data/collection etc only occurs when certain proximity or colocation is occurring

design principles:
- clear separation of components
  - intercommunication via specified applications
  - use of containers e.g. docker
- distinct data sources represented by distinct data stores - if one is leaked, only that data is exposed, not all data
- components are disconnected by default - reduce the attack surface - containers cannot talk to arbitrary cloud services - they will have to go through an export service
- all control and data flow logged for audit - log store for audit with tools to process logging information
  - how is data being used and moved/exported
  - data processing is transparent to users to allow better control and understanding

components:
databox
- docker hub with dev mode to run locally

Platform components - core
- container manager - managing apps, starting/stopping containers - UI/dashboard
- log store (separate container currently) to log all actions
- arbiter - minting tokens, permissions (separate container atm), root level catalogue uses hypercat with nested catalogues
- export service - data is taken off the box and sent elsewhere - specific set of requirements meaning that no data can leave the box without being permitted to do so by the user

Dynamic components that you may install to interact with services and data
- drivers - interact with services e.g. Hue, Twitter - drivers are containers. interaction via RestAPI with a data store attached for those logs
- apps process the data, where the computation is. Apps installed as containers with explicit permissions upon installation and provided by the arbiter to allow them to access specific data.

by default apps cannot talk to anything - data to leave needs to go via the export service

---

runs on x86 devices currently - laptops via d4mw
intel nooks
small arm devices will be possible, just not built the containers yet

----

Tosh

easy way for people to build apps quickly
databox sdk - cloud env for building databox applications

need GH account to use
sdk.iotdatabox.com

loading in an app - graphical programming environment allows you to drag in and connect nodes
allows debugging in the platform - see the output of the function you are using and what the function outputs

different input and output types for nodes e.g. bulbs for hue

hue
sensing driver for mobiles
os monitor driver
twitter

built in visualisations - graphs, lists etc

build, test, debug and publish

publish - takes graph, converts to code, puts it in a docker container, then can be run on the databox

manifest for apps: description of what your app can support and what it's going to do with the data, and which resources it needs
allows you to set different levels of functionality depending on corresponding devices in the home e.g. number of bulbs in the house.

puts the manifest into the app store, to allow databoxes to find it and download it..

---

Databox UI

tabs for apps, stores, drivers

driver queries the hub, adds data to store based on what is available (e.g. no of bulbs), allows you to install and agree to give the app access to those devices.

pulls up docker image, assigns permissions to image - then runs app.

lights demo - e2e run through of building app using sdk, getting it on the box

sdk designed for building apps, not drivers

----

Yousef - drivers

lower level development at the container level

app can talk to:
- stores (data and driver)
- arbiter
- export service

What makes an app?

app manifests: description, resources required, metadata, textual representation of permissions that the app might request, standard dockerfile (+ databox label, and UI port exposure details) to build app

environment variables: urls for containers to connect to, data source metadata in hypercat format, url for data source store, CA root certificate for the container for use over https (and a private key if you want to host on https server)

docker 1.13 - not passing secrets via environment variables. What about versioning the revision of the metadata? Currently just a repo of specs - would be good to add versioning. Repo to report issues:

overview:
- https communication
- rest apis
- direct mapping of http methods to crud functions
- pre-route granular permissions
- network-level isolation
- content security policy (CSP) to sandbox UIs

requesting tokens:
- SLA process updates arbiter wrt to permissions for that app
- arbiter checks these and will issue a token

reading/writing to/from stores
- websocket subscription events - for new data
- endpoints

dev workflow
- install docker and git
- clone databox
- launch in dev mode
- create dockerfile and manifest
- upload manifest to local manifest server
- build docker image and push to local registry
- browse to dashboard interface and launch

launch app as staging container....

exporting:
logs any requests on a small server run in the cloud - data export destination

----

driver manifest is simpler than an app manifest as it doesn't need to specify the data sources

environment variables - link to the datastore present in the manifest

----

components built so far
process by which you can build some

-----

Databox

mobile
home
cloud

not bound by home connectivity
phd student working on a personal vpn service - provides data and connectivity and capture data from all of your devices connected to that vpn - covers mobility issues

qi - export service

----

dev work group with Tosh
non dev work other side

-----
-----

Overall:

motivations for personal data ecosystem
- digital footprint -> inferences
- data generated by us -> social media, wearables, smartphones
- data around us -> iot devices etc

benefits
- public health, feedback

also major societal risks
- phorm, target, ashley madison

can we do detailed, user-centric, contextual analytics without privacy disasters and legal challenges?? also at a scalable rate?

databox: an open source personal networked system - NOT another data silo that acts as a honeypot

collates, curates, mediates access to personal data
cooperative environment at the user end

home -> cloud -> mobile

every data source comes with a driver and its own store
bring in other data, do all sorts of aggregations

app store as a way to approve apps to interact with databox - prototype like the Apple Store - to be demonstrated today
stores, drivers, apps, how apps get permissions from the arbiter and how they interact with the container manager

----
