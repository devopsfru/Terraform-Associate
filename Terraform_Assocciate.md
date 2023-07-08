For destroying reasource we can even specify the specific resource that we want to delete using below command.

Usage:

`teraform destroy -target reesourceprovidename.localrefname`

example:

`terraform destroy -target aws_instance.instancename`