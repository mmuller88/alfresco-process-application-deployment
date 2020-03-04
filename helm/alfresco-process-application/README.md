alfresco-process-application
============================
A Helm chart for an Alfresco Activiti Enterprise application

Current chart version is `7.1.0-M6`

Source code can be found [here](https://github.com/Alfresco/alfresco-process-application-deployment)

## Chart Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://activiti.github.io/activiti-cloud-helm-charts | activiti-cloud-audit | 7.1.311 |
| https://activiti.github.io/activiti-cloud-helm-charts | activiti-cloud-connector | 7.1.326 |
| https://activiti.github.io/activiti-cloud-helm-charts | activiti-cloud-notifications-graphql | 7.1.344 |
| https://activiti.github.io/activiti-cloud-helm-charts | activiti-cloud-query | 7.1.319 |
| https://activiti.github.io/activiti-cloud-helm-charts | runtime-bundle | 7.1.374 |
| https://kubernetes-charts.alfresco.com/stable | alfresco-adf-app | 2.1.3 |
| https://kubernetes-charts.alfresco.com/stable | alfresco-adf-app | 2.1.3 |
| https://kubernetes-charts.alfresco.com/stable | alfresco-process-springboot-service | 2.1.0 |
| https://kubernetes-charts.alfresco.com/stable | alfresco-process-springboot-service | 2.1.0 |
| https://kubernetes-charts.alfresco.com/stable | alfresco-process-springboot-service | 2.1.0 |
| https://kubernetes-charts.alfresco.com/stable | alfresco-process-springboot-service | 2.1.0 |
| https://kubernetes-charts.storage.googleapis.com | postgresql | 3.11.3 |
| https://kubernetes-charts.storage.googleapis.com | rabbitmq-ha | 1.38.1 |

## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| activiti-cloud-audit.enabled | bool | `true` |  |
| activiti-cloud-audit.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: KEYCLOAK_USERESOURCEROLEMAPPINGS\n  value: \"false\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n"` |  |
| activiti-cloud-audit.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| activiti-cloud-audit.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| activiti-cloud-audit.image.repository | string | `"quay.io/alfresco/alfresco-process-audit-service"` |  |
| activiti-cloud-audit.image.tag | string | `"7.1.0.M6"` |  |
| activiti-cloud-audit.ingress.enabled | bool | `true` |  |
| activiti-cloud-audit.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| activiti-cloud-audit.postgres.enabled | bool | `true` |  |
| activiti-cloud-audit.probePath | string | `"{{ tpl .Values.ingress.path . }}/actuator/health"` |  |
| activiti-cloud-connector.enabled | bool | `false` |  |
| activiti-cloud-connector.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n"` |  |
| activiti-cloud-connector.image.repository | string | `"activiti/example-cloud-connector"` |  |
| activiti-cloud-connector.image.tag | string | `"7.1.0.M6"` |  |
| activiti-cloud-connector.ingress.enabled | bool | `true` |  |
| activiti-cloud-connector.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| activiti-cloud-connector.nameOverride | string | `"example-cloud-connector"` |  |
| activiti-cloud-connector.probePath | string | `"{{ tpl .Values.ingress.path . }}/actuator/health"` |  |
| activiti-cloud-notifications-graphql.enabled | bool | `true` |  |
| activiti-cloud-notifications-graphql.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n"` |  |
| activiti-cloud-notifications-graphql.image.repository | string | `"quay.io/alfresco/alfresco-process-notifications-graphql-service"` |  |
| activiti-cloud-notifications-graphql.image.tag | string | `"7.1.0.M6"` |  |
| activiti-cloud-notifications-graphql.ingress.enabled | bool | `true` |  |
| activiti-cloud-notifications-graphql.ingress.path | string | `"/{{ .Release.Name }}/notifications"` |  |
| activiti-cloud-notifications-graphql.nameOverride | string | `"notifications"` |  |
| activiti-cloud-query.enabled | bool | `true` |  |
| activiti-cloud-query.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: KEYCLOAK_USERESOURCEROLEMAPPINGS\n  value: \"false\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n"` |  |
| activiti-cloud-query.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| activiti-cloud-query.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| activiti-cloud-query.image.repository | string | `"quay.io/alfresco/alfresco-process-query-service"` |  |
| activiti-cloud-query.image.tag | string | `"7.1.0.M6"` |  |
| activiti-cloud-query.ingress.enabled | bool | `true` |  |
| activiti-cloud-query.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| activiti-cloud-query.nameOverride | string | `"query"` |  |
| activiti-cloud-query.postgres.enabled | bool | `true` |  |
| activiti-cloud-query.probePath | string | `"{{ tpl .Values.ingress.path . }}/actuator/health"` |  |
| alfresco-admin-app.enabled | bool | `false` |  |
| alfresco-admin-app.env.APP_CONFIG_APPS_DEPLOYED | string | `"[{\"name\": \"{{ .Release.Name }}\" }]"` |  |
| alfresco-admin-app.env.APP_CONFIG_AUTH_TYPE | string | `"OAUTH"` |  |
| alfresco-admin-app.env.APP_CONFIG_BPM_HOST | string | `"{{ include \"common.gateway-url\" . }}"` |  |
| alfresco-admin-app.env.APP_CONFIG_IDENTITY_HOST | string | `"{{ include \"common.keycloak-url\" . }}/admin/realms/{{ include \"common.keycloak-realm\" . }}"` |  |
| alfresco-admin-app.image.pullPolicy | string | `"Always"` |  |
| alfresco-admin-app.image.repository | string | `"quay.io/alfresco/alfresco-admin-app"` |  |
| alfresco-admin-app.image.tag | string | `"7.1.0.M6"` |  |
| alfresco-admin-app.ingress.path | string | `"/{{ .Release.Name }}/admin"` |  |
| alfresco-admin-app.nameOverride | string | `"admin-app"` |  |
| alfresco-dmn-runtime-service.enabled | bool | `true` |  |
| alfresco-dmn-runtime-service.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n- name: ACT_RB_SERVICE_URL\n  value: '{{ include \"common.gateway-url\" . }}/{{ .Release.Name }}/rb'\n"` |  |
| alfresco-dmn-runtime-service.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| alfresco-dmn-runtime-service.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| alfresco-dmn-runtime-service.image.pullPolicy | string | `"Always"` |  |
| alfresco-dmn-runtime-service.image.repository | string | `"quay.io/alfresco/alfresco-dmn-runtime-service"` |  |
| alfresco-dmn-runtime-service.image.tag | string | `"7.1.0.M6"` |  |
| alfresco-dmn-runtime-service.ingress.enabled | bool | `true` |  |
| alfresco-dmn-runtime-service.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| alfresco-dmn-runtime-service.nameOverride | string | `"dmn-runtime"` |  |
| alfresco-dmn-runtime-service.postgres.enabled | bool | `true` |  |
| alfresco-dmn-runtime-service.probePath | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}/actuator/health"` |  |
| alfresco-dmn-runtime-service.rbac.create | bool | `false` |  |
| alfresco-dmn-runtime-service.serviceAccount.create | bool | `false` |  |
| alfresco-form-service.enabled | bool | `true` |  |
| alfresco-form-service.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n- name: ACT_RB_SERVICE_URL\n  value: '{{ include \"common.gateway-url\" . }}/{{ .Release.Name }}/rb'\n"` |  |
| alfresco-form-service.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| alfresco-form-service.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| alfresco-form-service.image.pullPolicy | string | `"Always"` |  |
| alfresco-form-service.image.repository | string | `"quay.io/alfresco/alfresco-form-service"` |  |
| alfresco-form-service.image.tag | string | `"7.1.0.M6"` |  |
| alfresco-form-service.ingress.enabled | bool | `true` |  |
| alfresco-form-service.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| alfresco-form-service.nameOverride | string | `"form"` |  |
| alfresco-form-service.postgres.enabled | bool | `true` |  |
| alfresco-form-service.probePath | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}/actuator/health"` |  |
| alfresco-form-service.rbac.create | bool | `false` |  |
| alfresco-form-service.serviceAccount.create | bool | `false` |  |
| alfresco-preference-service.enabled | bool | `true` |  |
| alfresco-preference-service.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n"` |  |
| alfresco-preference-service.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| alfresco-preference-service.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| alfresco-preference-service.image.pullPolicy | string | `"Always"` |  |
| alfresco-preference-service.image.repository | string | `"quay.io/alfresco/alfresco-preference-service"` |  |
| alfresco-preference-service.image.tag | string | `"7.1.0.M6"` |  |
| alfresco-preference-service.ingress.enabled | bool | `true` |  |
| alfresco-preference-service.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| alfresco-preference-service.nameOverride | string | `"preference"` |  |
| alfresco-preference-service.postgres.enabled | bool | `true` |  |
| alfresco-preference-service.probePath | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}/actuator/health"` |  |
| alfresco-preference-service.rbac.create | bool | `false` |  |
| alfresco-preference-service.serviceAccount.create | bool | `false` |  |
| alfresco-process-workspace-app.enabled | bool | `false` |  |
| alfresco-process-workspace-app.env.APP_CONFIG_APPS_DEPLOYED | string | `"[{\"name\": \"{{ .Release.Name }}\" }]"` |  |
| alfresco-process-workspace-app.env.APP_CONFIG_AUTH_TYPE | string | `"OAUTH"` |  |
| alfresco-process-workspace-app.env.APP_CONFIG_BPM_HOST | string | `"{{ include \"common.gateway-url\" . }}"` |  |
| alfresco-process-workspace-app.image.repository | string | `"quay.io/alfresco/alfresco-process-workspace-app"` |  |
| alfresco-process-workspace-app.image.tag | string | `"7.1.0.M6"` |  |
| alfresco-process-workspace-app.ingress.path | string | `"/{{ .Release.Name }}/workspace"` |  |
| alfresco-process-workspace-app.nameOverride | string | `"workspace-app"` |  |
| alfresco-script-runtime-service.enabled | bool | `true` |  |
| alfresco-script-runtime-service.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n"` |  |
| alfresco-script-runtime-service.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| alfresco-script-runtime-service.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| alfresco-script-runtime-service.image.pullPolicy | string | `"Always"` |  |
| alfresco-script-runtime-service.image.repository | string | `"quay.io/alfresco/alfresco-script-runtime-service"` |  |
| alfresco-script-runtime-service.image.tag | string | `"7.1.0.M6"` |  |
| alfresco-script-runtime-service.ingress.enabled | bool | `true` |  |
| alfresco-script-runtime-service.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| alfresco-script-runtime-service.nameOverride | string | `"script-runtime"` |  |
| alfresco-script-runtime-service.postgres.enabled | bool | `true` |  |
| alfresco-script-runtime-service.probePath | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}/actuator/health"` |  |
| alfresco-script-runtime-service.rbac.create | bool | `false` |  |
| alfresco-script-runtime-service.serviceAccount.create | bool | `false` |  |
| global.extraEnv | string | `""` | YAML formatted string to add extra environment properties to all deployments |
| global.gateway.annotations."kubernetes.io/ingress.class" | string | `"nginx"` |  |
| global.gateway.annotations."nginx.ingress.kubernetes.io/cors-allow-headers" | string | `"*"` |  |
| global.gateway.annotations."nginx.ingress.kubernetes.io/enable-cors" | string | `"true"` |  |
| global.gateway.domain | string | `"REPLACEME"` | gateway domain template, i.e. {{ .Release.Namespace }}.1.3.4.5.nip.io |
| global.gateway.host | string | `"gateway.{{ include \"common.gateway-domain\" . }}"` | global annotations for all service ingress resources |
| global.gateway.http | string | `"true"` |  |
| global.gateway.tlsacme | string | `"true"` |  |
| global.image.pullPolicy | string | `"Always"` |  |
| global.keycloak.host | string | `"identity.{{ include \"common.gateway-domain\" . }}"` | Keycloak host template, i.e. "identity.{{ .Release.Namespace }}.{{ .Values.global.gateway.domain }}" |
| global.keycloak.realm | string | `"alfresco"` | Keycloak realm |
| global.keycloak.resource | string | `"activiti"` |  |
| global.keycloak.url | string | `""` | full url to configure external Keycloak, https://keycloak.mydomain.com/auth |
| global.registryPullSecrets | list | `["quay-registry-secret"]` | Configure pull secrets for all deployments |
| postgres.enabled | bool | `true` |  |
| postgres.postgresqlPassword | string | `"password"` |  |
| postgres.resources.requests.cpu | string | `"350m"` |  |
| postgres.resources.requests.memory | string | `"512Mi"` |  |
| rabbitmq.enabled | bool | `true` |  |
| rabbitmq.ingress.annotations."kubernetes.io/ingress.class" | string | `"nginx"` |  |
| rabbitmq.ingress.annotations."nginx.ingress.kubernetes.io/cors-allow-headers" | string | `"*"` |  |
| rabbitmq.ingress.annotations."nginx.ingress.kubernetes.io/enable-cors" | string | `"true"` |  |
| rabbitmq.ingress.annotations."nginx.ingress.kubernetes.io/x-forwarded-prefix" | string | `"true"` |  |
| rabbitmq.ingress.enabled | bool | `false` |  |
| rabbitmq.ingress.hostName | string | `"REPLACEME"` |  |
| rabbitmq.ingress.path | string | `"/rabbitmq"` |  |
| rabbitmq.persistentVolume.enabled | bool | `true` |  |
| rabbitmq.rabbitmqErlangCookie | string | `"124567890abcdefghijklmnopqrstuv"` |  |
| rabbitmq.rabbitmqPassword | string | `"guest"` |  |
| rabbitmq.rabbitmqSTOMPPlugin.enabled | bool | `true` |  |
| rabbitmq.rabbitmqUsername | string | `"guest"` |  |
| rabbitmq.rbac.create | bool | `true` |  |
| rabbitmq.replicaCount | int | `1` |  |
| rabbitmq.resources.limits.cpu | int | `1` |  |
| rabbitmq.resources.limits.memory | string | `"2Gi"` |  |
| rabbitmq.resources.requests.cpu | string | `"350m"` |  |
| rabbitmq.resources.requests.memory | string | `"512Mi"` |  |
| rabbitmq.service.clusterIP | string | `"None"` |  |
| runtime-bundle.enabled | bool | `true` |  |
| runtime-bundle.extraEnv | string | `"- name: SERVER_PORT\n  value: \"8080\"\n- name: SERVER_SERVLET_CONTEXTPATH\n  value: \"{{ tpl .Values.ingress.path . }}\"\n- name: SERVER_USEFORWARDHEADERS\n  value: \"true\"\n- name: SERVER_TOMCAT_INTERNALPROXIES\n  value: \".*\"\n- name: MANAGEMENT_ENDPOINTS_WEB_EXPOSURE_INCLUDE\n  value: \"*\"\n- name: \"ACTIVITI_CLOUD_APPLICATION_NAME\"\n  value: \"{{ .Release.Name }}\"\n- name: ACT_KEYCLOAK_RESOURCE\n  value: \"{{ .Release.Name }}\"\n- name: KEYCLOAK_USERESOURCEROLEMAPPINGS\n  value: \"true\"\n"` |  |
| runtime-bundle.extraVolumeMounts | string | `"- name: license\n  mountPath: \"/root/.activiti/enterprise-license/\"\n  readOnly: true\n"` |  |
| runtime-bundle.extraVolumes | string | `"- name: license\n  secret:\n    secretName: licenseaps\n"` |  |
| runtime-bundle.image.repository | string | `"quay.io/alfresco/alfresco-process-runtime-bundle-service"` |  |
| runtime-bundle.image.tag | string | `"7.1.0.M6"` |  |
| runtime-bundle.ingress.enabled | bool | `true` |  |
| runtime-bundle.ingress.path | string | `"/{{ .Release.Name }}/{{ .Values.nameOverride }}"` |  |
| runtime-bundle.postgres.enabled | bool | `true` |  |
| runtime-bundle.probePath | string | `"{{ tpl .Values.ingress.path . }}/actuator/health"` |  |