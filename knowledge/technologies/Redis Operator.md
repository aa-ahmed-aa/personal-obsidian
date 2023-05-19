https://ot-redis-operator.netlify.app/docs/
to start using the operator first install the operator and then deploy redis standalone or cluster this second step will create pods for you that you will use later as your redis server

##### install the standalone version 

```
$ kubectl create ns ot-operators  
$ helm repo add ot-helm https://ot-container-kit.github.io/helm-charts/  
$ helm install redis-operator ot-helm/redis-operator --namespace ot-operators  
  
# Will install redis standalone to start using redis  
$ helm install redis ot-helm/redis --namespace ot-operators
```

then use `redis.ot-operators.svc.cluster.local` as your redis host to connect to redis on port `6379`

see also
- [[Helm]]