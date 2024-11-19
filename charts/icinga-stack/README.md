# Icinga Kubernetes Helm Charts

> **WARNING**: This chart is currently in alpha state and should not be used in production. Breaking changes in future releases are well possible.

[Icinga](https://icinga.com) is a monitoring system which checks the availability of your network resources, notifies users of outages, and generates performance data for reporting.

[Helm](https://helm.sh) is a tool for managing Kubernetes charts. Charts are packages of pre-configured Kubernetes resources.

This chart bootstraps a complete Icinga environment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager, optionally including the [Icinga Director](https://icinga.com/docs/director/latest/) and [Icinga Web 2](https://icinga.com/docs/webinterface/latest/).

## Installation

### Prerequisites

- Kubernetes 1.13+
- Helm 3+
- PV provisioner support in the underlying infrastructure
- Ingress controller for easier access to Icinga Web 2 from outside the cluster

### Add Helm repository

First you need to add the Icinga Helm repository to your Helm installation. Helm repositories are similar to package repositories in Linux distributions as in they contain different available packages of 
Kubernetes manifests for users to consume.

The Icinga Helm repository is hosted on GitHub Pages and can be added to your Helm installation by running the following command:

```console
helm repo add icinga https://icinga.github.io/helm-charts
helm repo update
```

### Install Icinga

Once the repository is known to your Helm installation, you can install Icinga by running the following command:

```console
helm install <release-name> \
  --set icinga2.config.ticket_salt.value=CHANGE-ME \
  --set icingaweb2.auth.admin_password.value=CHANGE-ME \
  --set global.api.users.director.password.value=CHANGE-ME \
  --set global.api.users.icingaweb.password.value=CHANGE-ME \
  --set global.databases.director.username.value=CHANGE-ME \
  --set global.databases.director.password.value=CHANGE-ME \
  --set global.databases.icingaweb2.username.value=CHANGE-ME \
  --set global.databases.icingaweb2.password.value=CHANGE-ME \
  --set global.databases.icingadb.username.value=CHANGE-ME \
  --set global.databases.icingadb.password.value=CHANGE-ME \
  --set global.databases.kubernetes.username.value=CHANGE-ME \
  --set global.databases.kubernetes.password.value=CHANGE-ME \
icinga/icinga-stack
```

This example sets all **required** value for the chart to install successfully. For more information on the available configuration options, see the [configuration](docs/configuration.md#configuration) section.

## Upgrading

Currently there's no upgrade path needed nor available. This will be added in the future.

## Reporting issues

Please report issues and bugs by creating a [GitHub Issue](https://github.com/icinga/helm-charts/issues/new/choose) and choosing **Bug** from the template list.
Continue by filling out the template with all the relevant information.

## Suggesting features and enhancements

Please suggest features and enhancements by creating a [GitHub Issue](https://github.com/icinga/helm-charts/issues/new/choose) and choosing **Feature Request** from the template list.
Continue by filling out the template with all the relevant information.

## Contributing

For information on how to contribute to this repository, see the [contribution guidelines](../../CONTRIBUTING.md).

## License

This chart is licensed under the terms of the [Apache 2.0](../../LICENSE) open source license.
