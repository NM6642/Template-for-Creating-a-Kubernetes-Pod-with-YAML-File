# Creating a Kubernetes Pod with YAML File

This guide outlines the steps to create a Kubernetes Pod using a YAML file (`pod.definition.yml`) and `kubectl`.

## Prerequisites

Before you begin, ensure you have the following:
- Kubernetes cluster running (e.g., Minikube, Docker Desktop with Kubernetes enabled)
- `kubectl` command-line tool configured to communicate with your Kubernetes cluster

## Steps to Set Up and Create a Kubernetes Pod

### Step 1: Create Directories

Create necessary directories for your project and navigate into the `pod` directory.

### Step 2: Write the Pod Definition YAML File

Create a file named `pod.definition.yml` and add the following content. Replace `your-image` with the Docker image you want to use.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
spec:
  containers:
    - name: your-image-container
      image: your-image

##Step 3: Create the Pod:
kubectl create -f pod.definition.yml
-This command reads the YAML file (pod.definition.yml) and creates the Pod defined within it.

##Step 4: Verify Pod Creation
kubectl get pods

##Optional Step 5: Interact with the Pod
##Get Pod Details
kubectl describe pod myapp-pod

##View Pod Logs
kubectl logs myapp-pod

