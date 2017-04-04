Steps
====================

Terraform version:
```
schu@master % terraform --version
Terraform v0.9.2
```

First time plan then apply:
```
schu@master % ./plan
Initializing the backend...


Successfully configured the backend "s3"! Terraform will automatically
use this backend unless the backend configuration changes.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your environment. If you forget, other
commands will detect it and remind you to do so if necessary.
Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.

The Terraform execution plan has been generated and is shown below.
Resources are shown in alphabetical order for quick scanning. Green resources
will be created (or destroyed and then created if an existing resource
exists), yellow resources are being changed in-place, and red resources
will be destroyed. Cyan entries are data sources to be read.

Your plan was also saved to the path below. Call the "apply" subcommand
with this plan file and Terraform will exactly execute this execution
plan.

Path: .terraform/tf.plan

+ aws_vpc.vpc
    assign_generated_ipv6_cidr_block: "false"
    cidr_block:                       "10.0.0.0/16"
    default_network_acl_id:           "<computed>"
    default_route_table_id:           "<computed>"
    default_security_group_id:        "<computed>"
    dhcp_options_id:                  "<computed>"
    enable_classiclink:               "<computed>"
    enable_dns_hostnames:             "<computed>"
    enable_dns_support:               "true"
    instance_tenancy:                 "<computed>"
    ipv6_association_id:              "<computed>"
    ipv6_cidr_block:                  "<computed>"
    main_route_table_id:              "<computed>"
    tags.%:                           "1"
    tags.Name:                        "bug maybe"


Plan: 1 to add, 0 to change, 0 to destroy.
schu@master % ./apply
aws_vpc.vpc: Creating...
  assign_generated_ipv6_cidr_block: "" => "false"
  cidr_block:                       "" => "10.0.0.0/16"
  default_network_acl_id:           "" => "<computed>"
  default_route_table_id:           "" => "<computed>"
  default_security_group_id:        "" => "<computed>"
  dhcp_options_id:                  "" => "<computed>"
  enable_classiclink:               "" => "<computed>"
  enable_dns_hostnames:             "" => "<computed>"
  enable_dns_support:               "" => "true"
  instance_tenancy:                 "" => "<computed>"
  ipv6_association_id:              "" => "<computed>"
  ipv6_cidr_block:                  "" => "<computed>"
  main_route_table_id:              "" => "<computed>"
  tags.%:                           "" => "1"
  tags.Name:                        "" => "bug maybe"
aws_vpc.vpc: Creation complete (ID: vpc-eb68798f)

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

The state of your infrastructure has been saved to the path
below. This state is required to modify and destroy your
infrastructure, so keep it safe. To inspect the complete state
use the `terraform show` command.

State path:

Outputs:

vpc_id = vpc-eb68798f
```

Have `.terraform/` folder:
```
schu@master % ls -al
total 48
drwxr-xr-x 4 admin admin 4096 Mar 20 17:33 ./
drwxr-xr-x 4 admin admin 4096 Mar 17 18:16 ../
-rwxr-xr-x 1 admin admin  102 Mar 17 18:29 apply*
-rw-r--r-- 1 admin admin  114 Mar 17 18:19 backend_config
drwxr-xr-x 8 admin admin 4096 Mar 20 17:32 .git/
-rw-r--r-- 1 admin admin   21 Mar 17 18:46 inputs.tf
-rw-r--r-- 1 admin admin  174 Mar 17 18:46 main.tf
-rw-r--r-- 1 admin admin   66 Mar 17 18:18 outputs.tf
-rwxr-xr-x 1 admin admin  230 Mar 17 23:22 plan*
-rw-r--r-- 1 admin admin 4581 Mar 17 18:42 README.md
drwxr-xr-x 2 admin admin 4096 Mar 20 17:33 .terraform/
schu@master % ls -al .terraform
total 12
drwxr-xr-x 2 admin admin 4096 Mar 20 17:33 ./
drwxr-xr-x 4 admin admin 4096 Mar 20 17:33 ../
-rw-r--r-- 1 admin admin  526 Mar 20 17:33 terraform.tfstate
```

Now, attempting to destroy:
```
schu@master % ./plan -destroy
Initializing the backend...
Backend configuration changed!

Terraform has detected that the configuration specified for the backend
has changed. Terraform will now reconfigure for this backend. If you didn't
intend to reconfigure your backend please undo any changes to the "backend"
section in your Terraform configuration.


Do you want to copy the state from "s3"?
  Would you like to copy the state from your prior backend "s3" to the
  newly configured "s3" backend? If you're reconfiguring the same backend,
  answering "yes" or "no" shouldn't make a difference. Please answer exactly
  "yes" or "no".

  Enter a value:
```

I was not expecting to see any re-initialization options prompts.
