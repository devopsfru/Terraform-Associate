For destroying reasource we can even specify the specific resource that we want to delete using below command.

Usage:

`teraform destroy -target reesourceprovidename.localrefname`

example:

`terraform destroy -target aws_instance.instancename`


after deleting the specific resource if you again do tf init it will again create that resource. if you dont wnt to create it again you have to remove  from tf file as well.

also you can delete the specific resource by commenting the resource block and run `terraform plan`

**Terraform statefile**

Terraform stores state of the infra we create in statefile

So it will map real resources on cloud with the configuration in the tf files.

it tracks infra data from .tfstate file