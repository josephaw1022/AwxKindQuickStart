# AWX Cluster Setup with Kind and Helm

This repository contains a Makefile with tasks to help you:

- Create a Kind cluster.
- Add the AWX Operator Helm repository.
- Inspect available AWX Operator chart versions and default values.
- Install or upgrade the AWX Operator using Helm (with optional version specification).
- Deploy an AWX instance into your cluster.

> **Note:** The Makefile uses dynamic help so that running `make` with no arguments will display a list of all available tasks.


## Quick Start Guide

This quick start guide will help you set up an AWX cluster using Kind and Helm with a single command.

```bash
curl -sSL https://raw.githubusercontent.com/josephaw1022/AwxKindQuickStart/main/quick-start.sh | bash
```

## Getting Started with the Makefile

### 0. Install Kind and Helm

Follow the official guidelines according to your OS:

- Kind: https://kind.sigs.k8s.io/docs/user/quick-start/
- Helm: https://helm.sh/docs/intro/install/

### 1. Create the Kind Cluster

Use the following command to create your Kind cluster:

```sh
make build-kind-cluster
```

If you need to delete the cluster later, run:

```sh
make delete-kind-cluster
```

### 2. Manage the AWX Operator Helm Chart

#### a. Add the AWX Helm Repository

```sh
make helm-repo-add
```

#### b. List Available AWX Operator Chart Versions

```sh
make helm-list-versions
```

#### c. Show Default Values for the AWX Operator Chart

```sh
make helm-get-values
```

### 3. Install/Upgrade the AWX Operator

To install or upgrade the AWX Operator using the Helm chart, run:

```sh
make helm-install-awx
```

If you want to install a specific version of the chart, specify the version using the `HELM_CHART_VERSION` variable. For example:

```sh
make helm-install-awx HELM_CHART_VERSION=2.19.1
```

### 4. Deploy the AWX Instance

After installing the AWX Operator, deploy an AWX instance (via the Custom Resource Definition) by applying the AWX manifest:

```sh
make awx-instance-apply
```

To delete the AWX instance later, run:

```sh
make awx-instance-delete
```

To obtain the AWX's admin credentials, run:

```sh
make awx-instance-password
```

---

## Additional Information

- **Dynamic Help:**  
  Running `make` with no arguments will dynamically list all available tasks along with their descriptions.

- **Configuration Variables:**  
  You can adjust configuration variables such as `KIND_CLUSTER_NAME`, `KIND_CONFIG_FILE`, `AWX_INSTANCE_FILE`, and `HELM_CHART_VERSION` in the Makefile as needed.
