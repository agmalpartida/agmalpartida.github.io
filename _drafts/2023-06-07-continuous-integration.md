---
layout: post
title: Continuous Integration and Continuous Deployment
date:   2023-06-07 19:40:16 +0200
categories: devops
---

**Continuous Integration**, AKA CI, is the practice of merging all developer working copies to a shared mainline multiple times a day. CI is the process of preparing a deployable application artifact, usually in an automated way triggered by a tool as Jenkins.

**Continuous Delivery** is a way in order to produce software in short cycles, ensuring that the software could be reliably released at any time, but which still relies on human intervention to determine what gets pushed into production.

**Continuous Deployment**, AKA CD, take continuous delivey a step further by automatically deploying all releases into production. Whereas continuous delivery mandates that software can be reliably released at any time, it doesn't requiere that every release is in fact released to production. CD is the process of releasing the artifact what we built on CI process into environments in an automated way.

## Shipping Sofware

Shipping software in a repeatable and reliable manner is hard to get. We need to build, validate and packaging a new version of our application for deployment, also we need to deploy our application through several stages as development, stage and production, and running it through several manual and automated steps before making it available to global users.
