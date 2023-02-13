getting started : https://argo-cd.readthedocs.io/en/stable/getting_started/

default user name is admin
default password for argocd is auto-generated and stored as clear text in the field `password` in a secret named `argocd-initial-admin-secret` you can edit the secret get the password and decode it for base64 using this comamnd `echo <PLAIN_TEXT_SECRET> | base64 --decode

#### FAQ
#### 1- issue with traefik expose using simple ingress resource 
in order to be able to expose argocd UI using ingress you need to enable insecure server by setting `server.insecure: "true"` in the `argocd-cmd-params-cm` ConfigMap 

small note in the [docs](https://argo-cd.readthedocs.io/en/stable/operator-manual/ingress/#traefik-v22) they mention smth about ingressRoute CRD for consuming gRPC but it doesn't work proberly just set insecure to true and create the ingress resource worked for me

more info here https://argo-cd.readthedocs.io/en/stable/operator-manual/ingress/

