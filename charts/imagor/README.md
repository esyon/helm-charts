# imagor

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/imagor)](https://artifacthub.io/packages/helm/esyon/imagor)
![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 8.8.1](https://img.shields.io/badge/AppVersion-8.8.1-informational?style=flat-square)

This is a HELM chart for imagor.

imagor is a fast, secure image processing server and Go library.

imagor uses one of the most efficient image processing library
[libvips](https://www.libvips.org/). It is typically 4-8x [faster](https://github.com/libvips/libvips/wiki/Speed-and-memory-use) than using the quickest ImageMagick and GraphicsMagick settings.
imagor implements libvips [streaming](https://www.libvips.org/2019/11/29/True-streaming-for-libvips.html) that facilitates parallel processing pipelines, achieving high network throughput.

imagor features a ton of image processing use cases, available as a HTTP server with first-class Docker support. It adopts the [thumbor](https://thumbor.readthedocs.io/en/latest/usage.html#image-endpoint) URL syntax representing a high-performance drop-in replacement.

imagor is a Go library built with speed, security and extensibility in mind. Alongside there is [imagorvideo](https://github.com/cshum/imagorvideo) bringing video thumbnail capability through ffmpeg C bindings.

Upstream links:
- [GitHub](https://github.com/cshum/imagor)

## Get Repo Info

```console
helm repo add esyon https://esyon.github.io/helm-charts
helm repo update
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release --namespace esyon esyon/imagor
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Upgrading Chart

```console
helm upgrade my-release esyon/imagor --install
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"shumc/imagor"` |  |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` | Set the annotations of the ingress |
| ingress.className | string | `""` | Set the class name of the ingress |
| ingress.enabled | bool | `false` | Set to true to enable ingress record generation. |
| ingress.hosts | list | `[]` | Set the hostnames of the ingress, see values.yaml for an example. |
| ingress.tls | list | `[]` | Set the TLS configuration for the ingress, see values.yaml for an example. |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| pdb.create | bool | `false` |  |
| pdb.maxUnavailable | string | `""` |  |
| pdb.minAvailable | int | `1` |  |
| pdb.unhealthyPodEvictionPolicy | string | `nil` | This is a beta feature, so it's not enabled by default. |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` | List of additional pod labels |
| podSecurityContext | object | `{}` |  |
| progressDeadlineSeconds | int | `120` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{ privileged: false, runAsUser: 1001 }`, except in OpenShift where `runAsUser` is not set. | Define the security context for the container. By default will use upstream recommended values. |
| service.annotations | object | `{}` | Annotations to add to the service |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `false` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. # If not set and create is true, a name is generated using the fullname template |
| strategy | object | `{}` |  |
| tolerations | list | `[]` |  |
| topologySpreadConstraints | list | `[]` |  |
| volumeMounts | list | `[]` |  |
| volumes | list | `[]` |  |