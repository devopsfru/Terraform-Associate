For destroying reasource we can even specify the specific resource that we want to delete using below command.

Usage:

`teraform destroy -target reesourceprovidename.localrefname`

example:

`terraform destroy -target aws_instance.instancename`


after deleting the specific resource if you again do tf init it will again create that resource. if you dont wnt to create it again you have to remove  from tf file as well.

also you can delete the specific resource by commenting the resource block and run `terraform plan`

## Terraform statefile

Terraform stores state of the infra we create in statefile

So it will map real resources on cloud with the configuration in the tf files.

it tracks infra data from .tfstate file

**Desired state vs Current state**

Desire state is at the terraform configuration/at the statefile level that it expect the infra state.

Current state is the state of the resource at the cloud provider ex: in the Azure portal


its always imp to match desired state to current. if not when you tun `tf plan` will inform you what actions need to take to make it equal to desired state.


Note:
When you create new resources like nsg and update vm with new nsg for the vm then after doing `terraform refresh` and `terraform plan` it gets the state but it wont create any thing since resource already exist.


because we never discribe a nsg group details in tf config file so it doesnt manage its state.

## Provider versioning

Terraform will have one version and Provider will have another.

if you dont specify the Provider version it takes most recent/latest version of that provider(aws/azure/gcp..)

we specify provider version under `terraform` and `required_providers` block

**Example:**

```bash
terraform {
    required_provders{
        aws = {
            source = "hashicorp/aws"
            version = "~> 3.0"
        }
    }
}
```

this could lead to compatibility issues so we do specify versions as mentined above

**Example arguments:**

| Logic              | operator      |
| ------------------ | ------------- |
| Greate than equal  | >=1.0         |
| Less than equals   | <=1.0         |
| Any version in 2.x | ~>2.0         |
| Any version b/w    | >=2.10,<=2.30 |
| exact              | =2.10         |

The details of this provider version you can find in `terraform.lock.hcl` file
you will gate provider registry, currene version and constraint details.

this lock file will help not to conflict with versions if you change the version in the tf directly.

you have to delte the lock file to avoid the conficlt, (not recommended in prod)

**upgrade**

we can override if we want to switch to updated version then change the version in tf fle and run `terraform init -upgrade`