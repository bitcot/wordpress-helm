# A Helm chart for Wordpress + MySQL Deployment

# WordPress

[WordPress](https://wordpress.org/) is one of the most versatile open
source content management systems on the market. A publishing platform
for building blogs and websites.

## **IMPORTANT NOTE**
This Chart was customized to work for my particular requirements.  No
guarantees it will work in your environment.

### Prerequisites
- Kubernetes 1.12+
- Helm 3.1.0

### Install HELM

Helm is a tool for managing Kubernetes charts. Charts are packages of pre-configured Kubernetes resources.

To install Helm, refer to the [Helm install guide](https://github.com/helm/helm#install) and ensure that the `helm` binary is in the `PATH` of your shell.

If you want to use a package manager:

- [Homebrew](https://brew.sh/) users can use `brew install helm`.
- [Chocolatey](https://chocolatey.org/) users can use `choco install kubernetes-helm`.

To rapidly get Helm up and running, start with the [Quick Start Guide](https://helm.sh/docs/intro/quickstart/).

See the [installation guide](https://helm.sh/docs/intro/install/) for more options,
including installing pre-releases.

### Using Helm

Once you have installed the Helm client, you can deploy a Bitnami Helm Chart into a Kubernetes cluster.

Please refer to the [Quick Start guide](https://helm.sh/docs/intro/quickstart/) if you wish to get running in just a few commands, otherwise the [Using Helm Guide](https://helm.sh/docs/intro/using_helm/) provides detailed instructions on how to use the Helm client to manage packages on your Kubernetes cluster.

Useful Helm Client Commands:
* View available charts: `helm search repo`
* Install a chart: `helm install my-release bitcot/<package-name>`
* Upgrade your application: `helm upgrade`

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release Chart-name
```

The command deploys WordPress on the Kubernetes cluster in the default
configuration. The [configuration](#configuration) section lists the
parameters that can be configured during installation.

## Execute the command to get the list of helm releases
```sh
helm list
```
## Execute the command to get the list of helm releases from all namespaceses
```sh
helm list -A
```

## Configuration

The following table lists the configurable parameters of the Bitcot chart and their default values.

| Parameter                | Description             | Default        |
| ------------------------ | ----------------------- | -------------- |
| `replicaCount` | Number of Pods to run | `1` |
| `namespace` | Kubernetes namespace | `"bitcot"` |
| `imagePullSecrets` | Secret Name | `[{"name": null}]` |
| `imageCredentials.registry` | Private Docker Registry | `null` |
| `imageCredentials.username` | Registry Name | `null` |
| `imageCredentials.password` | Registry Password | `null` |
| `imageCredentials.email` | Registry E-mail | `null` |
| `accessModes` | PVC Access mode | `["ReadWriteOnce"]` |
| `imagePullPolicy` | Image pull policy | `"Always"` |
| `storage` | PVC Storage | `"3Gi"` |
| `wordpress.tier` | Label for Wordpress | `"frontend"` |
| `wordpress.service.port` | Published Port | `80` |
| `wordpress.service.targetPort` | Target Port | `80` |
| `wordpress.service.protocol` | Port Protocol | `"TCP"` |
| `wordpress.service.type` | Kubernetes Service type | `"LoadBalancer"` |
| `wordpress.image` | Docker Image for Wordpress | `"wordpress:5.3"` |
| `wordpress.resources.requests.memory` | Requests of Memory for worpdress | `"500Mi"` |
| `wordpress.resources.requests.cpu` | Requests of CPU wordpress for wordpress | `"600m"` |
| `wordpress.resources.limits.memory` | Limits Memory for wordpress | `"600Mi"` |
| `wordpress.resources.limits.cpu` | Limits CPU for wordpress | `"750m"` |
| `wordpress.secrets.WORDPRESS_DB_HOST` | DB Host of the application | `"db host"` |
| `wordpress.secrets.WORDPRESS_DB_NAME` | DB Name of the application | `"db name"` |
| `wordpress.secrets.WORDPRESS_DB_PASSWORD` | Passoword of the application | `"random 8 character long alphanumeric string"` |
| `wordpress.secrets.WORDPRESS_DB_USER` | User of the application | `"user"` |
| `wordpress.containerPort` | Service HTTP port | `80` |
| `wordpress.containerPorthttps` | Service HTTPS port | `443` |
| `wordpress.Volumes.name` | PVC Name for Wordpress | `"wordpress-persistent-storage"` |
| `wordpress.Volumes.mountPath` | Volume Mount for Wordpress | `"/var/www/html"` |
| `Sidecar.name` | Sidecar Name | `"sidecar-container"` |
| `Sidecar.image` | Sidecar Image Used | `"ubuntu:20.04"` |
| `db.tier` | Label for Mysql | `"mysql"` |
| `db.service.port` | Published Port for mysql | `3306` |
| `db.service.targetPort` | Target Port for mysql | `3306` |
| `db.service.protocol` | Port Protocol | `"TCP"` |
| `db.service.type` | Kubernetes Service type | `"ClusterIP"` |
| `db.image` | Docker image for mysql | `"mysql:5.6"` |
| `db.resources.requests.memory` | Requests of Memory for mysql | `"500Mi"` |
| `db.resources.requests.cpu` | Requests of CPU wordpress for mysql | `"600m"` |
| `db.resources.limits.memory` | Limits Memory for mysql | `"600Mi"` |
| `db.resources.limits.cpu` | Limits CPU for mysql | `"750m"` |
| `db.secrets.MYSQL_DATABASE` | Database name to create | `"know2"` |
| `db.secrets.MYSQL_PASSWORD` | Password for the database | `"random 8 character long alphanumeric string"` |
| `db.secrets.MYSQL_ROOT_PASSWORD` | Mysql admin password | `"random 8 character long alphanumeric string"` |
| `db.secrets.MYSQL_USER` | Database user to create | `"wp_root"` |
| `db.containerPort` | Database port number | `3306` |
| `db.Volumes.name` | PVC Name for Mysql | `"mysql-persistent-storage"` |
| `db.Volumes.mountPath` | Volume Mount for Mysql | `"/var/lib/mysql"` |
| `initContainers.name` | Init Container Name | `"init-container-mysql"` |
| `initContainers.image` | Docker Image for Init Container | `"mysql:latest"` |
| `initContainers.Volume.name` | Volume Name | `"db-dump"` |
| `initContainers.Volume.mountPath` | Volume Mount for Init Container | `"/docker-entrypoint-initdb.d"` |

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the
chart and deletes the release.

## Authors

- [Bitcot](https://www.bitcot.com/)

![Logo](https://ca.slack-edge.com/T038JGHAM-U10U9592T-7448ec25ea73-54)

## Contact

Please reach out to us for queries and questions on `contact@bitcot.com`