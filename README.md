
# GFT Base activator repo

This repo has been develope to ptovide a hello world activator example and also provide you base image to build future activators.

You can use source code or you two provided packages. Curretly the following packages are avialble:

* helloworld
* actvator-base

Please see packages link in this repo to get more information related above
 packages.

We recommend to use the packages than the source code to install base
 activator but in case you want to use the source code, 
  you need to have terraform installed and project and service accounts have
   already been created.

After that please follow the following steps:

* Update connections.tf and add your service account file (json) to provider "google
", full directory to the your file shall be added to file("").
```hcl-terraform
provider "google" {
  credentials = file("")
  project     = var.cluster_project_id
  region      = var.region
}
```
* Update the following variable in variables.tf:
```hcl-terraform
variable "host_project_id" {
  description = "Project ID, example 'data-science-activator'"
  default     = ""
}
variable "zone" {
  description = "General zone of the project, example 'europe-west2-b'"
  default     = ""
}
variable "standard_subnetwork" {
  description = "VPC subnetwork such as main-network-subnet"
  default     = ""
}
variable "region" {
  description = "General location of the project, example 'europe-west2'"
  default     = ""
}
```

You can run terraform as follow:
```shell script
terraform init

terraform validate
 
terraform plan 

terraform apply
```

This activator builds the following components:
    
 
  
## Resources:
### GCE (Google Cloud Compute) 
Virtual machines that can be used to perform ETL tasks. This activator creates 1 virtual machines. The types of machine can be
 configured at terraform apply stage using the following variable:
 
 ```
 vms_machine_type: Machine type of the virtual both machines, example 'n1-standard-2'
 ``` 

### GCS (Google Cloud Storage)
In this activator, we creates one google storage buckets. 
 * landing-data-bucket: To be used for landing incoming data.
 
