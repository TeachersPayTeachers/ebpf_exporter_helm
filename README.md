# eBPF\_exporter
A prometheus exporter for custom eBPF metrics.

eBPF is an enchanment to BPF (Berkeley Packet Filter) and allow custom analysis
programs to be executed on Linux tracing tools.

This helm chart provides an easier way to export these metrics from a kubernetes cluster
and export it into prometheus.

## TL;DR;

1. Download repo
2. `helm install -n ebpf-exporter .`

## Links

* [eBPF](http://www.brendangregg.com/ebpf.html)
* [bcc](https://github.com/iovisor/bcc/blob/master/docs/reference_guide.md)
* [eBPF-exporter](https://github.com/cloudflare/ebpf_exporter)

## Tested OS
Since the bcc dependencies in the image are built for ubuntu the cluster will
most likely only run on cluster running ubuntu.

The tested OS is `Ubuntu 18.04 LTS, bionic` 

## Configuration

The following table lists the configurable parameters of the chart and their default values.

Parameter | Description | Default
--------- | ----------- | -------
`image.repository` | image repository | `vanneback/ebpf-exporter`
`image.tag` | image tag | `ubuntu`
`image.pullPolicy` |  image pull policy | `IfNotPresent`
`service.type` | service type | `ClusterIP`
`service.port` | service port | `80`
`service.annotations` | service annotations | `prometheus.io/scrape: \"true\"`
`ingress.enabled` | set to true if the service should be backed by an ingress | `false`
`ingress.annotations` | ingress annotations | `{}`
`ingress.paths` | list of available paths to ingress | `[]`
`ingress.hosts` | list of hosts to ingress | `chart-example.local`
`ingress.tls` | tls config of ingress | `[]`
`resources` | resource requests of the pods in the daemonset | `{}`
`configMapFile` | the program file ebpf will use (will replace the default one if specified) | `{}`
`podAnnotations` | annotations of pods in daemonset | `{}`
`nodeSelector` | node selector rules | `{}`
`tolerations` | node tolerations | `[]`
`affinity` | pod affinity rules | `{}`
`command` | supply alternate command to container | `{}`
`volumes` | additional volumes for the daemonset | `{}`
`volumeMounts` | additional volumeMounts for the daemonset | `{}`

## Docker file
The docker file to build images can be located at
<https://github.com/vanneback/ebpf_exporter_dockerfile>
