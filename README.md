# Cherre Container Deployment Example

This repo is a simple collection of code and template examples that should help others to understand how we, at Cherre, have standardized our deployment process. It is purely an example baseline and not a fixed guide. We've outlined the details of the Continuous Integration (CI) and Continuous Delivery (CD) pipeline we've generated at Cherre so that it can be replicated over and over. For more details about the accompanying Case Study, please read the published article here []. Bear in mind, the automated process is fluid and ever-changing so probably has already been updated. Our model is designed to continually allow greater flexibility whilst still standardizing and automating more and more of our stack.

## Core Tools Required

We heavily leverage Kubernetes for our application deployment to add additional flexibility to the yamls we use:

https://www.helm.sh and https://github.com/roboll/helmfile

### Plugins
Helm needs two plugins to work with our setup securely.

helm-gcs - Allows secure access to the chart repositories using Google Cloud credentials.

helm-secrets - Makes managing secrets in files secure.

### Install
`
helm plugin install https://github.com/nouney/helm-gcs
helm plugin install https://github.com/futuresimple/helm-secrets
`

### Values & Secrets Patterns
To be able to configure the environments differently, we use a standard file and directory structure.

* values.yaml
* secrets.yaml
* sandbox/values.yaml
* sandbox/secrets.yaml
* production/values.yaml
* production/secrets.yaml

Shared values and secrets are in the root directory of the chart. Values and secrets for each environment are kept in a directory matching the environment name.
