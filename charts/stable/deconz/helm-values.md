# Default Helm-Values

TrueCharts is primarily build to supply TrueNAS SCALE Apps.
However, we also supply all Apps as standard Helm-Charts. In this document we aim to document the default values in our values.yaml file.

Most of our Apps also consume our "common" Helm Chart.
If this is the case, this means that all values.yaml values are set to the common chart values.yaml by default. This values.yaml file will only contain values that deviate from the common chart.
You will, however, be able to use all values referenced in the common chart here, besides the values listed in this document.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Affinity constraint rules to place the Pod on a specific node. [[ref]](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity) |
| env | object | See below | environment variables. See [image docs](https://github.com/marthoc/docker-deconz/blob/master/README.md) for more details. |
| env.DECONZ_DEVICE | string | `nil` | Override the location where deCONZ looks for the RaspBee/Conbee device. |
| env.DECONZ_VNC_MODE | int | `1` | Enable VNC access to the container to view the deCONZ ZigBee mesh |
| env.DECONZ_VNC_PORT | int | `5900` | VNC server listen port |
| env.DECONZ_WEB_PORT | int | `8080` | Web UI listen port |
| env.DECONZ_WS_PORT | int | `6080` | Websocket listen port |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"tccr.io/truecharts/deconz"` | image repository |
| image.tag | string | `"v2.13.01@sha256:f43bf475d9d0cf6bc0700da1b10d5533e1eaea43f1a417a096ad8cafb033b249"` | image tag |
| persistence | object | See values.yaml | Configure persistence settings for the chart under this key. |
| podSecurityContext.runAsGroup | int | `0` |  |
| podSecurityContext.runAsUser | int | `0` |  |
| secret.DECONZ_VNC_PASSWORD | string | `""` |  |
| securityContext.readOnlyRootFilesystem | bool | `false` |  |
| securityContext.runAsNonRoot | bool | `false` |  |
| service | object | See values.yaml | Configures service settings for the chart. |

All Rights Reserved - The TrueCharts Project
