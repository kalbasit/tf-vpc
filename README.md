# tf-vpc
Terraform VPC module with Public/Private subnets support

# Usage

```hcl
module "vpc" {
  source = "github.com/kalbasit/tf-vpc"

  name = "vpc"
  cidr = "172.16.0.0/16"

  enable_dns_hostnames = true
  enable_dns_support   = true

  private_subnets = [
    "172.16.0.0/24",
    "172.16.1.0/24",
    "172.16.2.0/24",
    "172.16.3.0/24",
  ]

  public_subnets = [
    "172.16.4.0/24",
    "172.16.5.0/24",
    "172.16.6.0/24",
    "172.16.7.0/24",
  ]

  azs = [
    "us-east-1a",
    "us-east-1b",
    "us-east-1d",
    "us-east-1e",
  ]
}
```

# Module input variables

- `name` The name of the VPC
- `cidr` The CIDR of the VPC
- `public_subnets` A list of public subnets inside the VPC.
- `private_subnets` A list of private subnets inside the VPC.
- `azs` A list of Availability zones in the region
- `enable_dns_hostnames` should be true if you want to use private DNS within the VPC
- `enable_dns_support` should be true if you want to use private DNS within the VPC

# Outputs

- `private_subnets` A list of private subnet IDs
- `public_subnets` A list of public subnet IDs
- `vpc_id` The ID of the VPC
- `public_route_table_id` The ID of the public route table
- `private_route_table_id` The ID of the private route table

# License

All source code is licensed under the [MIT License](LICENSE).
