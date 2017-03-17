Steps
====================


```
schu@master % aws s3 ls --recursive s3://schu.eu-west-1.terraform-remote-state/
schu@master % git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

Run `./plan`, which will init:
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

schu@master ?:1 % git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .terraform/

nothing added to commit but untracked files present (use "git add" to track)
schu@master ?:1 % ll .terraform
total 20K
drwxr-xr-x 2 admin admin 4.0K Mar 17 18:33 ./
drwxr-xr-x 4 admin admin 4.0K Mar 17 18:33 ../
-rw-r--r-- 1 admin admin  526 Mar 17 18:33 terraform.tfstate
-rw-r--r-- 1 admin admin 4.1K Mar 17 18:33 tf.plan
```

`./apply` it:
```
schu@master ?:1 % ./apply
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
aws_vpc.vpc: Creation complete (ID: vpc-dd293eb9)

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

The state of your infrastructure has been saved to the path
below. This state is required to modify and destroy your
infrastructure, so keep it safe. To inspect the complete state
use the `terraform show` command.

State path:

Outputs:

vpc_id = vpc-dd293eb9
schu@master ?:2 % git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .terraform/
        terraform.tfstate

nothing added to commit but untracked files present (use "git add" to track)
schu@master ?:2 % aws s3 ls --recursive s3://schu.eu-west-1.terraform-remote-state/
schu@master ?:2 %
```
