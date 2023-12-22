For your enjoyment, Terraform GKE cluster creation files...

main.tf - This file holds the majority of the logic used to create the cluster.  It utilizes a few google cloud modules for access and networking, then fires up the gke module to get into the core of the task.

variables.tf - This is where some key configurations can be changed. Most important would be cluster_name and env_name. Other items like region and various networking elements are named here.

output.tf - Currently the only item output is the cluster name on completion of cluster creation.

Useful commands:

There are various ways to run these commands on the GCP environment.  For testing I used...
"gcloud container clusters get-credentials --zone us-central1 space-cluster-pacman"

Once you can access the environment the typical terraform workflow follows...
terraform init
terraform apply

...or for the more cautious...
terraform init
terraform validate
terraform plan -out "runfile.txt"
terraform apply "runfile.txt"

The cluster can be cleaned up with good ol...
terraform destroy