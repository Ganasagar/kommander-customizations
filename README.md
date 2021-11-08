# kommander-customizations




###Pre-reqs
1. A Konvoy 2.0 cluster provisioned 
2. Access to internet
3. Helm 3 installed


###Install 

Kommander ships in a Helm chart, so prior to installing Kommander, make Helm aware of the Helm repository providing the Kommander chart:

```bash
helm repo add kommander https://mesosphere.github.io/kommander/charts
helm repo update
```

###Modify the values file listed in this repo. You can update the values files to mark addons as `true` or `false`
```bash
vim values.yaml
```

###Install the helm-chart with custom values file
```bash
helm install --values=values.yaml -n kommander --create-namespace kommander-bootstrap kommander/kommander-bootstrap --version=${VERSION} --set certManager=$(kubectl get ns cert-manager > /dev/null 2>&1 && echo "false" || echo "true")
```
