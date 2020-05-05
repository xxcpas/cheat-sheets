# Helm commands

## Definitions

* A **Chart** is a Helm package. It contains all of the resource definitions necessary to run an application, tool, or service inside of a Kubernetes cluster.
* A **Repository** is the place where charts can be collected and shared. 
* A **Release** is an instance of a chart running in a Kubernetes cluster. One chart can often be installed many times into the same cluster. And each time it is installed, a new release is created. 

Helm installs *charts* into Kubernetes, creating a new *release* for each installation. And to find new charts, you can search Helm chart *repositories*.

## Finding charts

Search charts in the repositories added locally with `helm repo add`:
```sh
helm3 search repo [filter]
```

This will display a list of chart names and versions. 

```
NAME         	CHART VERSION	APP VERSION	DESCRIPTION
gloo/gloo    	1.3.15       	           	Gloo Helm chart for Kubernetes
glooe/gloo-ee	1.2.12       	           	A Helm chart for Kubernetes
```

## Installing a package

We install a package with

```sh
helm3 install glooe glooe/gloo-ee --namespace kube-gloo
```
where `glooe` = release name, `glooe/gloo-ee` = chart name

After installation, view the release state:
```sh
helm3 status glooe -n kube-gloo
```
*Output:*
```
NAME: glooe
LAST DEPLOYED: Tue Mar 31 17:19:55 2020
NAMESPACE: kube-gloo
STATUS: deployed
REVISION: 1
TEST SUITE: None
```

We can see the availabe values to customize the chart:

```sh
helm3 show values glooe/gloo-ee
```

## Viewing deployed releases

```sh
helm3 list -n kube-gloo
```
*Output:*
```
NAME 	NAMESPACE	REVISION	UPDATED                              	STATUS  	CHART         	APP VERSION
glooe	kube-gloo	1       	2020-03-31 17:19:55.193216 +0200 CEST	deployed	gloo-ee-1.2.12
```

We can view the chart overriden values of a release:

```sh
helm3 get values glooe -n kube-gloo
```

and the effective manifests of a release:

```sh
helm3 get manifests glooe -n kube-gloo
```
