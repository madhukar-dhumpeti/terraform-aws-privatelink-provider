# terraform-aws-privatelink-provider

[![Terraform Version](https://img.shields.io/badge/Terraform%20Version->=0.12.0,<=0.13.0-blue.svg)](https://releases.hashicorp.com/terraform/)
[![Release](https://img.shields.io/github/release/traveloka/terraform-aws-privatelink-provider.svg)](https://github.com/traveloka/terraform-aws-privatelink-provider/releases)
[![Last Commit](https://img.shields.io/github/last-commit/traveloka/terraform-aws-privatelink-provider.svg)](https://github.com/traveloka/terraform-aws-privatelink-provider/commits/master)
[![Issues](https://img.shields.io/github/issues/traveloka/terraform-aws-privatelink-provider.svg)](https://github.com/traveloka/terraform-aws-privatelink-provider/issues)
[![Pull Requests](https://img.shields.io/github/issues-pr/traveloka/terraform-aws-privatelink-provider.svg)](https://github.com/traveloka/terraform-aws-privatelink-provider/pulls)
[![License](https://img.shields.io/github/license/traveloka/terraform-aws-privatelink-provider.svg)](https://github.com/traveloka/terraform-aws-privatelink-provider/blob/master/LICENSE)
![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.png?v=103)

## Description

A Terraform module which creates an AWS VPC Endpoint Service for service provider PrivateLink.

## Table of Content

* [terraform-aws-privatelink-provider](#terraform-aws-privatelink-provider)
   * [Description](#description)
   * [Table of Content](#table-of-content)
   * [Prerequisites](#prerequisites)
   * [Dependencies](#dependencies)
   * [Usage](#usage)
   * [Terraform Version](#terraform-version)
   * [Requirements](#requirements)
   * [Providers](#providers)
   * [Modules](#modules)
   * [Resources](#resources)
   * [Inputs](#inputs)
   * [Outputs](#outputs)
   * [Contributing](#contributing)
   * [Authors](#authors)
   * [License](#license)

## Prerequisites

In order to provision this module, it is require some information from an existing resources as input parameter, those resources are:

- Network Load Balancer, input variable that require the information from this resource are, `nlb_arns`

## Dependencies

Doesn't have any dependencies to any other Terraform module

## Usage

```hcl
module "service-provider-privatelink" {
  source         = "github.com/traveloka/terraform-aws-privatelink-provider?ref=master"
  nlb_arns       = ["arn:aws:elasticloadbalancing:ap-southeast-1:012345678901:loadbalancer/net/service-provider-nlb/01ab234c5d67e8f9"]
  service_name   = "abctest"
  product_domain = "abc"
  environment    = "staging"
  description    = "VPC Endpoint Service for service abctest"

  # Optional
  allowed_principals  = ["arn:aws:iam::<aws-account-id>:root"]
  acceptance_required = false
}
```

## Terraform Version

The latest stable version of Terraform which this module tested working is Terraform `0.12.31` on 2021/09/23

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

No requirements.

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | n/a |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_vpc_endpoint_service.service_provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_endpoint_service) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_acceptance_required"></a> [acceptance\_required](#input\_acceptance\_required) | Whether or not VPC endpoint connection requests to the service must be accepted by the service owner | `string` | `false` | no |
| <a name="input_additional_tags"></a> [additional\_tags](#input\_additional\_tags) | Additional tags to be added to the endpoint service | `map` | `{}` | no |
| <a name="input_allowed_principals"></a> [allowed\_principals](#input\_allowed\_principals) | List of all whitelisted AWS principals which will create Interface VPC Endpoint to connect to this Endpoint Service | `list` | `[]` | no |
| <a name="input_description"></a> [description](#input\_description) | Description of the Endpoint Service | `string` | `""` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | Will be used in resources' Environment tag | `string` | n/a | yes |
| <a name="input_nlb_arns"></a> [nlb\_arns](#input\_nlb\_arns) | List of all NLB ARNs which associate with the Endpoint Service | `list` | n/a | yes |
| <a name="input_product_domain"></a> [product\_domain](#input\_product\_domain) | Abbreviation of the product domain the created resources belong to | `string` | n/a | yes |
| <a name="input_service_name"></a> [service\_name](#input\_service\_name) | Stack name of the Endpoint Service | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_service_provider_name"></a> [service\_provider\_name](#output\_service\_provider\_name) | The name of VPC Endpoint Service |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Contributing

This module accepting or open for any contributions from anyone, please see the [CONTRIBUTING.md](https://github.com/traveloka/terraform-aws-privatelink-provider/blob/master/CONTRIBUTING.md) for more detail about how to contribute to this module.

## Authors

- [Febry Antonius](https://github.com/febryantonius)

## License

This module is under Apache License 2.0 - see the [LICENSE](https://github.com/traveloka/terraform-aws-privatelink-provider/blob/master/LICENSE) file for details.