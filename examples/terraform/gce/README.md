# GCE Quickstart Terraform scripts

The GCE Quickstart Terraform scripts can be used to create the needed infrastructure for a Kubernetes HA cluster.
Check out the following [GCE getting started walkthrough][gce-quickstart] to learn more about how to use the
scripts and how to provision a Kubernetes cluster using KubeOne.

[gce-quickstart]: https://github.com/kubermatic/kubeone/blob/master/docs/quickstart-gce.md

## GCE Provider configuration

### Credentials

Per https://www.terraform.io/docs/providers/google/provider_reference.html#configuration-reference
ether of the following ENV variables should be accessible:
* `GOOGLE_CREDENTIALS`
* `GOOGLE_CLOUD_KEYFILE_JSON`
* `GCLOUD_KEYFILE_JSON`

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| cluster\_name | prefix for cloud resources | string | n/a | yes |
| cluster\_network\_cidr | Cluster network subnet cidr | string | `"10.240.0.0/24"` | no |
| control\_plane\_count | Number of instances | string | `"3"` | no |
| control\_plane\_image\_family | Image family to use for provisioning instances | string | `"ubuntu-1804-lts"` | no |
| control\_plane\_image\_project | Project of the image to use for provisioning instances | string | `"ubuntu-os-cloud"` | no |
| control\_plane\_target\_pool\_members\_count |  | string | `"3"` | no |
| control\_plane\_type | GCE instance type | string | `"n1-standard-2"` | no |
| control\_plane\_volume\_size | Size of the boot volume, in GB | string | `"100"` | no |
| project | Project to be used for all resources | string | n/a | yes |
| region | GCP region to speak to | string | `"europe-west3"` | no |
| ssh\_agent\_socket | SSH Agent socket, default to grab from $SSH_AUTH_SOCK | string | `"env:SSH_AUTH_SOCK"` | no |
| ssh\_port | SSH port | string | `"22"` | no |
| ssh\_public\_key\_file | SSH public key file | string | `"~/.ssh/id_rsa.pub"` | no |
| ssh\_username | Username to provision with the ssh_public_key_file | string | `"kubeadmin"` | no |
| workers\_type | GCE instance type | string | `"n1-standard-2"` | no |
| workers\_volume\_size | Size of the boot volume, in GB | string | `"100"` | no |

## Outputs

| Name | Description |
|------|-------------|
| kubeone\_api | kube-apiserver LB endpoint |
| kubeone\_hosts | Control plane endpoints to SSH to |
| kubeone\_workers | Workers definitions, that will be transformed into MachineDeployment object |

