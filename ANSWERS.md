# HW4 — Short Answers

## 1. Rolling-update safety
With `maxUnavailable: 0`, Kubernetes won't terminate an old pod until its replacement passes the readiness probe, so all 3 replicas keep serving throughout an update. With `maxUnavailable: 1`, one old pod can be removed before a new one is ready, so capacity could briefly drop to 2 of 3 and requests may be dropped or slowed under load.

## 2. Health probes
`/health` is a cheap check that doesn't need Redis or the model, so pods go Ready quickly and reliably. `/predict` is slower and depends on Redis and scoring, so using it would make probes flaky, add load, and could cause healthy pods to be pulled from the Service or restarted just because a dependency was slow.

## 3. Autoscaling under load
If request volume doubled, CPU per pod would climb past 40% and the HPA would add replicas, up to the maximum of 8, to bring utilization back near the target. Once it hits 8 it cannot scale further, so CPU would stay above 40% and latency and errors would rise until traffic drops or the max is raised.

## AI disclosure
I used Claude (Anthropic) to help draft these answers and to walk through the assignment steps. I reviewed the answers and can explain them.
