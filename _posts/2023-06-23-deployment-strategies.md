---
layout: post
title: Deployment Strategies
date:   2023-06-23 23:15:00 +0200
categories: devops
---

There are several strategies you can use for application deployment, depending on your requirements.
For instance, we have 5 copies of a old version of your application running and we want to roll out a new one. A few of the strategies that it could be use:

- **Rolling deployment with replacement**: Take down 1 of the old copies of the app, deploy a new copy to replace it, wait for the new copy to come up and pass health checks, start sending the new copy live traffic, and then repeat the process until all the old copies have been replaced. Rolling deployment with replacement ensures that you never have more than 5 copies of the app running, which could be useful if you have limited capacity, or if you’re dealing with a stateful system where each app has a unique identity. This deployment strategy can work with larger batch sizes and that during deployment, you will have both the old and new versions of the app running at the same time.

- **Rolling deployment without replacement**: Deploy 1 new copy of the app, wait for the new copy to come up and pass health checks, start sending the new copy live traffic, undeploy an old copy of the app, and then repeat the process until all the old copies have been replaced. Rolling deployment without replacement works only if you have flexible capacity (i.e., your apps run in the cloud) and if your application can tolerate more than 5 copies of it running at the same time. The advantage is that you never have less than 5 copies of the app running, so you’re not running at a reduced capacity during deployment. This deployment strategy can work with larger batch sizes and that during deployment, you will have both the old and new versions of the app running at the same time.

- **Blue-green deployment**: Deploy 5 new copies of the app, wait for all of them to come up and pass health checks, shift all live traffic to the new copies, and then undeploy the old copies. Blue-green deployment works only if you have flexible capacity, for instance, if you are deploying in the cloud, and if your application can tolerate more than 5 copies of it running at the same time. The advantage is that only one version of your app is visible to users at any given time, and that you never have less than 5 copies of the app running, so you’re not running at a reduced capacity during deployment.

![cicd](/img/cicd-blue.jpg){:style="display:block; margin-left:auto; margin-right:auto"}{: width="800" }
![cicd](/img/cicd-green.jpg){:style="display:block; margin-left:auto; margin-right:auto"}{: width="800" }

- **Canary deployment**: Deploy 1 new copy of the app, wait for it to come up and pass health checks, start sending live traffic to it, and then pause the deployment. During the pause, compare the new copy of the app, called the "canary", to one of the old copies, called the "control". You can compare the canary and control across a variety of dimensions: CPU usage, memory usage, latency, throughput, error rates in the logs, HTTP response codes, and so on. Ideally, there’s no way to tell the two copies apart, which should give you confidence that the new code works just fine. In that case, you unpause the deployment, and use one of the rolling deployment strategies to complete it. On the other hand, if you spot any differences, then that may be a sign of problems in the new code, and you can cancel the deployment and undeploy the canary before the problem gets worse.

![cicd](/img/cicd-canary-during.png){:style="display:block; margin-left:auto; margin-right:auto"}{: width="800" }
![cicd](/img/cicd-canary-post.png){:style="display:block; margin-left:auto; margin-right:auto"}{: width="800" }
