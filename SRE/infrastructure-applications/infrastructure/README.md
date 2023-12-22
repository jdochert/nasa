For your enjoyment, Terraform GKE cluster creation files...

main.tf - This file holds the majority of the logic used to create the cluster.  It utilizes a few google cloud modules for access and networking, then fires up the gke module to get into the core of the task.

variables.tf - This is where some key configurations can be changed. Most important would be cluster_name and env_name. Other items like region and various networking elements are named here.

output.tf - Currently the only item output is the cluster name on completion of cluster creation.

Useful commands:

Once you can access the environment the typical terraform workflow follows... <br>
terraform init <br>
terraform apply <br>

...or for the more less adventurous... <br>
terraform init <br>
terraform validate <br>
terraform plan -out "runfile.txt" <br>
terraform apply "runfile.txt" <br>

The cluster can be cleaned up with good ol... <br>
terraform destroy

After the cluster is running, to access it with kubectl you could run this... <br>
"gcloud container clusters get-credentials --zone us-central1 space-cluster-pacman" <br>
