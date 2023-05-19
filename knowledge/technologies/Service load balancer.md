
when you are using tools like [[kind]], [[microk8s]], [[K3S]] or [[K3D]] these service will create cluster in this context cluster means controleplane nodes and agents(worker nodes) in in this context you will need a wrapper load balancer to manage the load for those nodes(or master nodes) this is what [[metalLB]] to provice services of type loadBalancer


see also
- [[devspace]]