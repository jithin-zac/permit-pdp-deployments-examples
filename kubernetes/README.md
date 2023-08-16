# Deploying PDP using raw Kubernetes YAMLs
In this example, we will show you how to deploy the Permit PDP on Kubernetes using raw YAMLs.

Resources included in this example:
- Deployment
- Service
- Secret

## To deploy the PDP on Kubernetes, follow these steps:
1. Download the YAML files from this directory.
2. Replace the `PDP_API_KEY` value in the `secret.yaml` file with your API key.
3. Create a new namespace for the PDP - e.g.  `kubectl create namespace permit-pdp` (You can choose which namespace you want).
4. Apply the YAML files - `kubectl apply -f .` - make sure you are in the directory that contains the YAML files.
5. (Optional) Wait for the PDP to be ready - `kubectl wait --for=condition=available --timeout=600s deployment/permit-pdp -n permit-pdp`

Once the PDP is ready, you can start sending authorization requests to it.

## Interacting with the PDP
To interact with the PDP **internally** (from inside the cluster), you can use the service name `permit-pdp.<Your Namespace>.svc.cluster.local`.

To interact with the PDP **externally** (from outside the cluster), you'll need to expose the service using a load balancer or an ingress of your choice.
