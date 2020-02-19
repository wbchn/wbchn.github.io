[TOC]

# QUESTION 1

## Company Overview

Mountkirk Games makes online, session-based, multiplayer games for the most popular mobile platforms.

Company Background

Mountkirk Games builds all of their games with some server-side integration, and has historically used cloud providers to lease physical servers. A few of their games were more popular than expected, and they had problems scaling their application servers, MySQL databases, and analytics tools.

Mountkirk’s current model is to write game statistics to files and send them through an ETL tool that loads them into a centralized MySQL database for reporting.

Solution Concept

Mountkirk Gamesis building a new game, which they expect to be very popular. They plan to deploy the game’s backend on Google Compute Engine so they can capture streaming metrics, run intensive analytics, and take advantage of its autoscaling server environment and integrate with a managed NoSQL database.

Technical Requirements

Requirements for Game Backend Platform

1. Dynamically scale up or down based on game activity

2. Connect to a managed NoSQL database service

3. Run customize Linux distro

Requirements for Game Analytics Platform

1. Dynamically scale up or down based on game activity

2. Process incoming data on the fly directly from the game servers

3. Process data that arrives late because of slow mobile networks

4. Allow SQL queries to access at least 10 TB of historical data

5. Process files that are regularly uploaded by users’ mobile devices

6. Use only fully managed services

CEO Statement

Our last successful game did not scale well with our previous cloud provider, resulting in lower user adoption and affecting the game’s reputation. Our investors want more key performance indicators (KPIs) to evaluate the speed and stability of the game, as well as other metrics that provide deeper insight into usage patterns so we can adapt the game to target users.

CTO Statement

Our current technology stack cannot provide the scale we need, so we want to replace MySQL and move to an environment that provides autoscaling, low latency load balancing, and frees us up from managing physical servers.

CFO Statement

We are not capturing enough user demographic data, usage metrics, and other KPIs. As a result, we do not engage the right users, we are not confident that our marketing is targeting the right users, and we are not selling enough premium Blast-Ups inside the games, which dramatically impacts our revenue.

**A. Overview**

## QUESTION 2

Mountkirk Games wants you to design their new testing strategy. How should the test coverage differ from their existing backends on the other platforms?

**A. Tests should scale well beyond the prior approaches**

B. Unit tests are no longer required, only end-to-end tests

C. Tests should be applied after the release is in the production environment

D. Tests should include directly testing the Google Cloud Platform (GCP) infrastructure

## QUESTION 3: 

Mountkirk Games has deployed their new backend on Google Cloud Platform (GCP). You want to create a through testing process for new versions of the backend before they are released to the public. You want the testing environment to scale in an economical way. How should you design the process?

**A. Create a scalable environment in GCP for simulating production load**

B. Use the existing infrastructure to test the GCP-based backend at scale

C. Build stress tests into each component of your application using resources internal to GCP to simulate load

D. Create a set of static environments in GCP to test different levels of load - for example, high, medium, and low

## QUESTION 4: 

Mountkirk Games wants to set up a continuous delivery pipeline. Their architecture includes many small services that they want to be able to update and roll back quickly. Mountkirk Games has the following requirements:
Services are deployed redundantly across multiple regions in the US and Europe Only frontend services are exposed on the public internet.They can provide a single frontend IP for their fleet of services Deployment artifacts are immutable.Which set of products should they use?

A. Google Cloud Storage, Google Cloud Dataflow, Google Compute Engine

B. Google Cloud Storage, Google App Engine, Google Network Load Balancer

**C. Google Kubernetes Registry, Google Container Engine, Google HTTP(S) Load Balancer**

D. Google Cloud Functions, Google Cloud Pub/Sub, Google Cloud Deployment Manager

## QUESTION 5: 

Mountkirk Games' gaming servers are not automatically scaling properly. Last month, they rolled out a new feature, which suddenly became very popular. A record number of users are trying to use the service, but many of them are getting 503 errors and very slow response times. What should they investigate first?

A. Verify that the database is online

**B. Verify that the project quota hasn't been exceeded**

C. Verify that the new feature code did not introduce any performance bugs

D. Verify that the load-testing team is not running their tool against production

## QUESTION 6: 

Mountkirk Games needs to create a repeatable and configurable mechanism for deploying isolated application environments. Developers and testers can access each other's environments and resources, but they cannot access staging or production resources. The staging environment needs access to some services from production.What should you do to isolate development environments from staging and production?

**A. Create a project for development and test and another for staging and production**

B. Create a network for development and test and another for staging and production

C. Create one subnetwork for development and another for staging and production

D. Create one project for development, a second for staging and a third for production

## QUESTION 7: 

Mountkirk Games wants to set up a real-time analytics platform for their new game. The new platform must meet their technical requirements.Which combination of Google technologies will meet all of their requirements?

A. Kubernetes Engine, Cloud Pub/Sub, and Cloud SQL

**B. Cloud Dataflow, Cloud Storage, Cloud Pub/Sub, and BigQuery**

C. Cloud SQL, Cloud Storage, Cloud Pub/Sub, and Cloud Dataflow

D. Cloud Dataproc, Cloud Pub/Sub, Cloud SQL, and Cloud Dataflow

E. Cloud Pub/Sub, Compute Engine, Cloud Storage, and Cloud Dataproc

# QUESTION 1: 

## Company Overview

Mountkirk Games makes online, session-based, multiplayer games for mobile platforms. They build all of their games using some server-side integration.

Historically, they have used cloud providers to lease physical servers.

Due to the unexpected popularity of some of their games, they have had problems scaling their global audience, application servers, MySQL databases, and analytics tools.

Their current model is to write game statistics to files and send them through an ETL tool that loads them into a centralized MySQL database for reporting.

Solution Concept

Mountkirk Games is building a new game, which they expect to be very popular. They plan to deploy the game’s backend on Google Compute Engine so they can capture streaming metrics, run intensive analytics, and take advantage of its autoscaling server environment and integrate with a managed NoSQL database.

Business Requirements

Increase to a global footprint.

Improve uptime – downtime is loss of players.

Increase efficiency of the cloud resources we use.

Reduce latency to all customers.

Technical Requirements

Requirements for Game Backend Platform

Dynamically scale up or down based on game activity.

Connect to a transactional database service to manage user profiles and game state.

Store game activity in a timeseries database service for future analysis.

As the system scales, ensure that data is not lost due to processing backlogs.

Run hardened Linux distro.

Requirements for Game Analytics Platform

Dynamically scale up or down based on game activity

Process incoming data on the fly directly from the game servers

Process data that arrives late because of slow mobile networks

Allow queries to access at least 10 TB of historical data

Process files that are regularly uploaded by users’ mobile devices

Executive Statement

Our last successful game did not scale well with our previous cloud provider, resulting in lower user adoption and affecting the game’s reputation. Our investors want more key performance indicators (KPIs) to evaluate the speed and stability of the game, as well as other metrics that provide deeper insight into usage patterns so we can adapt the game to target users. Additionally, our current technology stack cannot provide the scale we need, so we want to replace MySQL and move to an environment that provides autoscaling, low latency load balancing, and frees us up from managing physical servers.

**A. Overview**

## QUESTION 2: 

For this question, refer to the Mountkirk Games case study. Mountkirk Games wants to migrate from their current analytics and statistics reporting model to one that meets their technical requirements on Google Cloud Platform.Which two steps should be part of their migration plan? (Choose two.)

**A. Evaluate the impact of migrating their current batch ETL code to Cloud Dataflow.**

**B. Write a schema migration plan to denormalize data for better performance in BigQuery.**

C. Draw an architecture diagram that shows how to move from a single MySQL database to a MySQL cluster.

D. Load 10 TB of analytics data from a previous game into a Cloud SQL instance, and run test queries against the full dataset to confirm that they complete successfully.

E. Integrate Cloud Armor to defend against possible SQL injection attacks in analytics files uploaded to Cloud Storage.

## QUESTION 3: 

For this question, refer to the Mountkirk Games case study. You need to analyze and define the technical architecture for the compute workloads for your company, Mountkirk Games. Considering the Mountkirk Games business and technical requirements, what should you do?

A. Create network load balancers. Use preemptible Compute Engine instances.

B. Create network load balancers. Use non-preemptible Compute Engine instances.

**C. Create a global load balancer with managed instance groups and autoscaling policies. Use preemptible Compute Engine instances.**

D. Create a global load balancer with managed instance groups and autoscaling policies. Use non-preemptible Compute Engine instances.

## QUESTION 4: 

For this question, refer to the Mountkirk Games case study. Mountkirk Games wants to design their solution for the future in order to take advantage of cloud and technology improvements as they become available. Which two steps should they take? (Choose two.)

A. Store as much analytics and game activity data as financially feasible today so it can be used to train machine learning models to predict user behavior in the future.

B. Begin packaging their game backend artifacts in container images and running them on Kubernetes Engine to improve the availability to scale up or down based on game activity.

**C. Set up a CI/CD pipeline using Jenkins and Spinnaker to automate canary deployments and improve development velocity.**

D. Adopt a schema versioning tool to reduce downtime when adding new game features that require storing additional player data in the database.

**E. Implement a weekly rolling maintenance process for the Linux virtual machines so they can apply critical kernel patches and package updates and reduce the risk of 0-day vulnerabilities.**

## QUESTION 5: 

For this question, refer to the Mountkirk Games case study. Mountkirk Games wants you to design a way to test the analytics platform's resilience to changes in mobile network latency. What should you do?

A. Deploy failure injection software to the game analytics platform that can inject additional latency to mobile client analytics traffic.

B. Build a test client that can be run from a mobile phone emulator on a Compute Engine virtual machine, and run multiple copies in Google Cloud Platform regions all over the world to generate realistic traffic.

**C. Add the ability to introduce a random amount of delay before beginning to process analytics files uploaded from mobile devices.**

D. Create an opt-in beta of the game that runs on players' mobile devices and collects response times from analytics endpoints running in Google Cloud Platform regions all over the world.

## QUESTION 6: 

For this question, refer to the Mountkirk Games case study. You need to analyze and define the technical architecture for the database workloads for your company, Mountkirk Games. Considering the business and technical requirements, what should you do?

A. Use Cloud SQL for time series data, and use Cloud Bigtable for historical data queries.

B. Use Cloud SQL to replace MySQL, and use Cloud Spanner for historical data queries.

C. Use Cloud Bigtable to replace MySQL, and use BigQuery for historical data queries.

**D. Use Cloud Bigtable for time series data, use Cloud Spanner for transactional data, and use BigQuery for historical data queries.**

## QUESTION 7: 

For this question, refer to the Mountkirk Games case study. Which managed storage option meets Mountkirk's technical requirement for storing game activity in a time series database service?

**A. Cloud Bigtable**

B. Cloud Spanner

C. BigQuery

D. Cloud Datastore

## QUESTION 8: 

For this question, refer to the Mountkirk Games case study. You need to analyze and define the technical architecture for the compute workloads for you company, Mounkirk Games. Considering the Mountkirk games business and technical requirements, what should you do?

A. Create network load balancers. Use preemptible Compute Engine instances.

B. Create network load balancers. Use non-preemptible Compute Engine instances.

**C. Create a global load balancer with managed instance groups and autoscaling policies. Use preemptible Compute Engine instances.**

D. Create a global load balancer with managed instance groups and autoscaling policies. Use non-preemptible Compute Engine instance.

## QUESTION 9: 

For this question, refer to the Mountkirk Games case study. You are in charge of the new Game Backend Platform architecture. The game communicates with the backend over a REST API.You want to follow Google-recommended practices. How should you design the backend?

A. Create an instance template for the backend. For every region, deploy it on a multi-zone managed instance group. Use an L4 load balancer.

B. Create an instance template for the backend. For every region, deploy it on a single-zone managed instance group. Use an L4 load balancer.

**C. Create an instance template for the backend. For every region, deploy it on a multi-zone managed instance group. Use an L7 load balancer.**

D. Create an instance template for the backend. For every region, deploy it on a single-zone managed instance group. Use an L7 load balancer.

