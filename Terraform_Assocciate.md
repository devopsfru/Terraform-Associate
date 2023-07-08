For destroying reasource we can even specify the specific resource that we want to delete using below command.

Usage:

`teraform destroy -target reesourceprovidename.localrefname`

example:

`terraform destroy -target aws_instance.instancename`


after deleting the specific resource if you again do tf init it will again create that resource. if you dont wnt to create it again you have to remove  from tf file as well.

also you can delete the specific resource by commenting the resource block and run `terraform plan`