# Keycloak on Kubernetes

## Generate configurations

```bash
kubectl kustomize overlays/local
```  
or  
```bash
kubectl apply -k overlays/local
```

## Secrets

```yaml
apiVersion: v1
metadata:
  name: keycloak-secret
kind: Secret
stringData:
  database_host: {{database_host}}
  database_port: "{{database_port}}"
  database_password: {{database_password}}
  database_ssl_params: trustCertificateKeyStoreUrl=file:///tmp/keycloak/aws_rds.jks&trustCertificateKeyStorePassword={{trust_keystore_password}}&verifyServerCertificate=true&useSSL=true&requireSSL=true
```

## AWS RDS

To connect to AWS RDS over SSL generate Java Keystore (JKS) file from AWS RDS keys  

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html  
https://stackoverflow.com/a/29997111  
