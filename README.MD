#### AWS VPC Terraform Module

This Terraform Module creates a VPC with *High Availability* and gets the first *2 Available Zones* automatically and enables VPC Peering within the same AWS Account.

* Creates a custom VPC with CIDR Block
* Internet Gateway with VPC Association
* Creates Public, Private and Database Subnets in each AZ (*1a and 1b*)
* Elastic IP
* Creates NAT Gateway in Public Subnets for Private Subnets internet access
* Creates Public, Private and Database Route Tables
* Subnets and Route Tables Association
* VPC Peering if user requests
* Adding the Peering Route in default VPC, if user don't provide acceptor VPC explicitly
* Adding the Peering Routes in Public, Private and Database Route Tables

### Inputs
* project_name (Required) - Your Project Name
* environment_name (Required) - which Environment you are working in
* vpc_cidr (Optional) - Default value is 10.0.0.0/16, user can override
* enable_dns_hostnames (Optional) - default value is true
* comman_tags (Optional) - better to provide
* vpc_tags (Optional) - default value is empty. type is map
* igw_tags (Optional) - default value is empty. type is map
* public_subnets_cidr (Required) - user must provide 2 valid public subnets CIDR
* public_subnets_tags (Optional) - default value is empty. type is map
* private_subnets_cidr (Required) - user must provide 2 valid private subnets CIDR
* private_subnets_tags (Optional) - default value is empty. type is map
* database_subnets_cidr (Required) - user must provide 2 valid database subnets CIDR
* database_subnets_tags (Optional) - default value is empty. type is map
* nat_gateway_tags (Optional) - default value is empty. type is map
* public_route_table_tags (Optional) - default value is empty. type is map
* private_route_table_tags (Optional) - default value is empty. type is map
* database_route_table_tags (Optional) - default value is empty. type is map
* is_peering_required (Optional) - default value is false
* acceptor_vpc_id (Optional) - default value is default VPC ID
* vpc_peering_tags (Optional) - default value is empty. type is map

### Outputs
* vpc_id - VPC ID Created
* public_subnet_ids - 2 public subnet IDs created
* private_subnet_ids - 2 private subnet IDs created
* database_subnet_ids - 2 database subnet IDs created