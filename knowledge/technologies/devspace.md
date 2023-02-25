https://www.devspace.sh

devspace is a tool to speed up the development of microservices architecture

how it works : https://www.devspace.sh/docs/getting-started/introduction?.#how-does-it-work

## How does it work?[​](https://www.devspace.sh/docs/configuration/dev/modifications/#how-does-it-work "Direct link to heading")

When any modifications are defined for a dev container, DevSpace will do the following:

1.  Find the Kubernetes pod that contains the dev container according to the [selectors](https://www.devspace.sh/docs/configuration/dev/selectors/) defined for this dev container.
2.  Find the replica owner that this pod was created from (e.g. Deployment, StatefulSet, etc.)
3.  Scale down the replica number for the replica owner object, i.e. set `replicas: 0` for the Deployment, StatefulSet, etc.
4.  Clone the replica owner object to create a new Deployment/StatefulSet with the name `[old-object-name]-devspace`
5.  Apply the modifications to the newly created Deployment/StatefulSet, e.g. swap out the image, add env vars, etc.
6.  Wait until the a new pod was created from the new Deployment/StatefulSet

### streaming logs 
https://www.devspace.sh/docs/configuration/dev/connections/terminal#stream-logs

### file sync 
https://www.devspace.sh/docs/configuration/dev/connections/file-sync

