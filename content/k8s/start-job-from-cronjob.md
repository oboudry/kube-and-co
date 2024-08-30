+++
title = 'Start Job From Cronjob'
date = 2024-08-30T14:39:31+02:00
draft = true
+++

# Start a job run from a scheduled cronjob in Kubernetes

For testing purpose it's often interesting to be able tu run a job directly
from a cronjob definition.

```sh
kubectl create job --from=cronjob/<name-of-cronjob> <name-of-new-job>
```
