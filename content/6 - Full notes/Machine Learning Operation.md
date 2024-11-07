---
date created: Sat, Mar 2nd 2024, 3:47 am
date modified: Wed, Nov 6th 2024, 3:23 pm
tags:
  - ml/MLops
---

# lifescycle:

Design, development, Deployment
iterative cycle, not meaning that you won't back to the design phrase if you are doing development phase.
The machine learning lifecycle is an iterative and cyclical process where it is not uncommon to go back and forth between phases.

I believe the MLOps is likely developed because only few theoretical machine learning model can be really applied in business environment, or in the reality.

Having a structured process, for instance, by using these phases, can greatly help in tackling this problem!`

Involved
Data engineer, Data scientist, Software engineer
![[DE,DS,SDE.png]]

Speed
Accuracy
Transparency
is more importance in ml, as we need to know why model makes prediction, why it is wrong, and how we can improve the model

Data ingestion is the process of obtaining, importing, and processing data for later use or storage in a database

an Application Programming Interface (API) allows for communication between services. This allows your application to communicate data to and from the machine learning model.
![[API.png]]

CI/CD pipeline
CI: continuous integration, practices while codes is being written
CD: continuous deployment, practices after coding is complete
![[MLops-1.png]]

Deployment strategies
basic: new model for production, send all new data only to new model
shadow: send new data to both new and old, still use old for production
canary: use new as production only for small part of incoming data.
![[MLops-2.png]]
