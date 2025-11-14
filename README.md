# Voting App

This repository contains the manifests and configurations needed to deploy the Voting App on Kubernetes using Minikube.

## Overview

The Voting App consists of two main components:

* **Vote UI** – A simple frontend where users can cast votes.
* **Result UI** – A dashboard displaying the tally of votes.

Both components are exposed using Ingress resources and can be accessed using custom hostnames.

## Prerequisites

* Kubernetes cluster (Minikube recommended)
* `kubectl` installed and configured
* `minikube` installed
* Administrator/root access to edit `/etc/hosts`

## Accessing the Application

To reach the application using the hostnames `vote.local` and `result.local`, follow these steps:

1. Start Minikube tunnel:

   ```bash
   minikube tunnel
   ```

2. Copy the **external IP** of the Ingress service.

3. Edit your `/etc/hosts` file and map both hostnames to the external IP:

   ```
   <EXTERNAL-IP> vote.local
   <EXTERNAL-IP> result.local
   ```

## Deployment

Deploy all application manifests using:

```bash
kubectl apply -f .
```

This will create all required Deployments, Services, and Ingress resources.

## Notes

* Ingress may take a few moments to assign an external IP.
* `minikube tunnel` must remain running to keep the external IP reachable.

## Troubleshooting

* If the UI loads without CSS/JS, ensure the Ingress annotation for `ingress.class` matches your environment.
* Verify hostnames resolve correctly using `ping vote.local` or `ping result.local`.
