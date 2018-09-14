# Certbot Openshift (Cloudflare)

A template for generating/replacing OpenShift route certificates using letsencrypt and Cloudflare.

## Installation

Once for each namespace, run the following:

```bash
oc project test-project
oc process -f requirements-template.yaml CLOUDFLARE_EMAIL=cloudflare@example.com CLOUDFLARE_API_KEY=0123456789abcdef0123456789abcdef01234567 | oc create -f -
```

Then, for each service, run the following:

```bash
oc process -f template.yaml ROUTE_NAME=test-service SERVICE_NAME=test-service HOST_NAME=test.apps.example.com | oc create -f -
```
