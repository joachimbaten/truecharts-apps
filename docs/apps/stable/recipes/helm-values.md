# Default Helm-Values

TrueCharts is primarily build to supply TrueNAS SCALE Apps.
However, we also supply all Apps as standard Helm-Charts. In this document we aim to document the default values in our values.yaml file.

Most of our Apps also consume our "common" Helm Chart.
If this is the case, this means that all values.yaml values are set to the common chart values.yaml by default. This values.yaml file will only contain values that deviate from the common chart.
You will, however, be able to use all values referenced in the common chart here, besides the values listed in this document.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalContainers.nginx.image | string | `"{{ .Values.nginxImage.repository }}:{{ .Values.nginxImage.tag }}"` |  |
| additionalContainers.nginx.name | string | `"nginx"` |  |
| additionalContainers.nginx.ports[0].containerPort | int | `80` |  |
| additionalContainers.nginx.ports[0].name | string | `"main"` |  |
| additionalContainers.nginx.volumeMounts[0].mountPath | string | `"/etc/nginx/nginx.conf"` |  |
| additionalContainers.nginx.volumeMounts[0].name | string | `"recipes-config"` |  |
| additionalContainers.nginx.volumeMounts[0].readOnly | bool | `true` |  |
| additionalContainers.nginx.volumeMounts[0].subPath | string | `"nginx-config"` |  |
| additionalContainers.nginx.volumeMounts[1].mountPath | string | `"/media"` |  |
| additionalContainers.nginx.volumeMounts[1].name | string | `"media"` |  |
| additionalContainers.nginx.volumeMounts[2].mountPath | string | `"/static"` |  |
| additionalContainers.nginx.volumeMounts[2].name | string | `"static"` |  |
| env | object | See below | environment variables. See [project docs](https://raw.githubusercontent.com/vabene1111/recipes/master/.env.template) for more details. |
| envValueFrom.POSTGRES_HOST.secretKeyRef.key | string | `"plainhost"` |  |
| envValueFrom.POSTGRES_HOST.secretKeyRef.name | string | `"dbcreds"` |  |
| envValueFrom.POSTGRES_PASSWORD.secretKeyRef.key | string | `"postgresql-password"` |  |
| envValueFrom.POSTGRES_PASSWORD.secretKeyRef.name | string | `"dbcreds"` |  |
| envValueFrom.SECRET_KEY.secretKeyRef.key | string | `"SECRET_KEY"` |  |
| envValueFrom.SECRET_KEY.secretKeyRef.name | string | `"recipes-secrets"` |  |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"tccr.io/truecharts/recipes"` | image repository |
| image.tag | string | `"v1.0.3@sha256:293f8d08b8326899e9ce0f4c4c8ffac521c22f168290ddfa0db1da0b81bda296"` | image tag |
| nginxImage.repository | string | `"tccr.io/truecharts/nginx"` | nginx sidecar image repository |
| nginxImage.tag | string | `"v1.21.4@sha256:361630c9cc477122ee5af45acab2c6acd192b0fef6ecbd7203c8d78aa2d16996"` | nginx sidecar image tag |
| persistence | object | See values.yaml | Configure persistence settings for the chart under this key. |
| podSecurityContext.runAsGroup | int | `0` |  |
| podSecurityContext.runAsUser | int | `0` |  |
| postgresql.enabled | bool | `true` |  |
| postgresql.existingSecret | string | `"dbcreds"` |  |
| postgresql.postgresqlDatabase | string | `"recipes"` |  |
| postgresql.postgresqlUsername | string | `"recipes"` |  |
| securityContext.readOnlyRootFilesystem | bool | `false` |  |
| securityContext.runAsNonRoot | bool | `false` |  |
| service | object | See values.yaml | Configures service settings for the chart. |

All Rights Reserved - The TrueCharts Project
