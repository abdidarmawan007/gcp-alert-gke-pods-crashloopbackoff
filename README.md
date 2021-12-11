# Alert pods crashloopbackoff
- GCP GKE
- GCP Cloud Monitoring + GCP Cloud Logging
- Slack

## Create logs based metric
- Metric Type : Counter
- Unit 1
##### You can exclude from deployment with name production-worker-xxx because to many restart resource.labels.pod_name!~ "production-worker"
```
resource.type="k8s_pod"
resource.labels.cluster_name="production-zeus"
resource.labels.namespace_name="production"
jsonPayload.message="Back-off restarting failed container"
resource.labels.pod_name!~ "production-worker"
```
![alt text](https://i.imgur.com/liyeeO8.png)

##### Create alert from metric
![alt text](https://i.imgur.com/7O6L0jt.png)

## Choose a metric from log we create before
![alt text](https://i.imgur.com/UWeWH35.png)

![alt text](https://i.imgur.com/58YXXIs.png)

## Example alert from slack channel
![alt text](https://i.imgur.com/1tYmTxt.png)
![alt text](https://i.imgur.com/t9Za64Y.png)
