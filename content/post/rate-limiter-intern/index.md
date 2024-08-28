---
author: nldxtd
title: Backend service intern, at MicroSoft
date: 2024-08-15
---

As my last internship which marks the end of my undergraduate study, I was given the chance of involving in the rate-limiter service at Microsoft, China.

Generally speaking, it's a pleasant journey along with those teammates work together, using my knowledge learned in class and also to validate my cs foundation, especially in the field of Operating-System and backend service field which I currently plan to dive into.

## Problems

Rate limiter service is part of the ai-inferencing service which we call it a micro-service, customs use our service to do batch inferencing. But resources like GPUs are limited from the inferencing engine, so before inferencing can really take place, there must be a rule to define how many inference unit a single batch request can take. So the problem we are facing is:

The basic server side
- The ability to handle concurrency request
    - The system architechture
- Set up as part of the inference micro-service
The additional design
- How to store and calculate the used quota
- Enable the share between different tenant of same group and fairness issue.

## Practice

### System Architechture Design: Multi-Replica Deployment

- 2 replica per region
- 30 pods per replica
- 7 shards of redis, tenants from the same group will be projected to the same shard

We use ASP.NET core as the backend framework and redis as cache. And there are 60 instances in total to serve traffic per region. The CI/CD set is provided by Azure platform which can take a long time to deploy honestly. Everytime we have an update to the current repo, we use a rolling update strategy, which is 3 by 3 in the 60 instances, whenever there is a failure discovered through the readiness api, we roll back to the last version.

Problem is discovered that sometimes when traffic is high, the request is stuck at a point in getting lock of a required service (like some kind of authorization). This is weird and we suspected it's due to the framework itself, dead lock probably. But we didn't get into this problem that far because this problem happened occasionally.

### Microservice, frontdoor to the inference engine

