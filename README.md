# Cleanup Old Pods CronJob

This repository provides a Kubernetes CronJob configuration for automatically cleaning up old pods in a specified namespace. The CronJob runs every minute and deletes pods that are older than 30 days and have a status of `Succeeded`.

## Components

1. **CronJob**: A Kubernetes CronJob that schedules the cleanup task to run every minute.
2. **ConfigMap**: Contains a shell script used by the CronJob to identify and delete old pods.
3. **ServiceAccount**: A Kubernetes ServiceAccount used by the CronJob to interact with the Kubernetes API.
4. **Role**: Defines the necessary permissions for the ServiceAccount to list, get, and delete pods.


## Prerequisites
-- **Kubernetes CLI (kubectl)**: Ensure you have kubectl installed and configured to access your Kubernetes cluster.
-- **jq**: The script uses jq to parse JSON. Make sure jq is installed on your system.


## How It Works

1. **Namespace Definition**: The script targets the `default` namespace. You can modify the `NAMESPACE` variable in the script to target a different namespace.
2. **Date Calculation**: The script calculates the cutoff date to determine which pods are older than 30 days.
3. **Pod Selection**: It retrieves all pods in the specified namespace that are in the `Succeeded` phase.
4. **Pod Deletion**: Pods older than 30 days are selected and deleted.

## How To Apply
Just use command **kubectl apply -f .** and make sure you are in the right directory where all the yaml are present.
