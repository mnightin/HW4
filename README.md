# DATA 789 HW4 — Scale It

Deployed the TrustBank fraud service (ghcr.io/rfsalas/trustbank-fraud) to Minikube with 3 replicas, resource limits, probes, a LoadBalancer Service, and an HPA (40% CPU, max 8).
Run it with `bash scripts/local_up.sh`, then `kubectl apply -f k8s/`.
Rolling update, blue-green, and Azure Container Apps steps follow README-hw4.md.
Evidence is in `screenshots/`, short answers are in `ANSWERS.md`.
