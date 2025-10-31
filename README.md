This repository contains the configuration files to deploy a production-ready PostgreSQL instance on Red Hat OpenShift, managed through Argo CD (GitOps).
The setup follows best practices for security, persistence, and automation, ensuring a consistent and auditable database deployment.

Components:

PostgreSQL Deployment (v15)
Persistent Volume Claim (PVC) for durable storage
Kubernetes Secret for credentials
ClusterIP Service for internal access
Kustomize overlays for environment management (e.g., prod)
Argo CD Application manifest for automated deployment

Prerequisites
OpenShift 4.16+ cluster
Argo CD (or OpenShift GitOps Operator) installed
StorageClass available for PVCs (e.g., ocs-storagecluster-ceph-rbd)

Deploy via Argo CD
oc apply -f postgresql/argocd-app.yaml -n openshift-gitops

Verify Deployment
oc get pods -n postgresql-prod
oc get svc -n postgresql-prod

Accessing PostgreSQL
psql -h postgres.postgresql-prod.svc.cluster.local -U turbo_user -d turbo


