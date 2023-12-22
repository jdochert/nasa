Kubernetes and Kustomizations

I found the documentation for Kustomize to be extremly flawed and challenging to work with.  The project appears to be in a state of transition making for alot of outdated material out there.  I did get through it though and I do see the advantages of using kustomize in regards to limiting duplication of code and ease of supported many environments.

Following the Kustomize directory structure I laid out a dev and prod environment.  After GKE cluster creation the following commands will setup each environment...

To launch the dev environment run the following from the kustomize folder...<br>
kubectl apply -k overlays/dev

Key details for dev: <br>
dev is set to use a smaller autoscale group 1/2<br>
dev is served through a simple external load balancer that forwards traffic from port 88 to 9898 on the pod.

To launch the prod environment run the following from the kustomize folder...<br>
kubectl apply -k overlays/prod

Key details for prod: <br>
prod is set to use a larger autoscale group 2/4<br>
dev is served through a ingress on port 80 that then passes traffic back to 9898 on the pods.
