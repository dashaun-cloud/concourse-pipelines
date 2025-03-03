# concourse-pipelines
Centralized CI

### Login to Concourse

```bash
fly login -c https://concourse.dashaun.cloud -t live
```

```bash
fly -t live set-pipeline -p hello-world -c sample-pipelines/hello-world.yaml
```

### Create Team

```bash
fly -t live set-team --team-name javagrunt-com --github-org=javagrunt-com --github-user=pinkemma --github-user=colabottles

fly -t live set-team --team-name dashaun-demo --github-org=dashaun-demo --github-user=pinkemma --github-user=colabottles --github-user=thiagochirana
```

```bash
fly -t live set-team --team-name javagrunt-com -c team-config/javagrunt-com.yaml
```

### Advisor Server

```bash
./gradlew :application-advisor-server:bootRun --args='--server.port=8090 --debug'
```


### Tanzu Laptop

```bash
export POD_NAME=$(kubectl get pods --namespace concourse -l "app=concourse-web" -o jsonpath="{.items[0].metadata.name}")
kubectl port-forward --namespace concourse $POD_NAME 9000:9000
```
> Make sure to use http://127.0.0.1:9000 instead of http://localhost:9000
