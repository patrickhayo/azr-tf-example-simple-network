# azr-tf-module-template

[Terraform](https://www.terraform.io) Module to create **[NAME]** in Azure

<!-- BEGIN_TF_DOCS -->
## Prerequisites

- [Terraform](https://releases.hashicorp.com/terraform/) v0.12+

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) | >=3.0.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | >=3.0.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_bastion_host"></a> [bastion\_host](#module\_bastion\_host) | github.com/patrickhayo/modules//bastionhost | n/a |
| <a name="module_nat"></a> [nat](#module\_nat) | github.com/patrickhayo/modules//nat | n/a |
| <a name="module_network"></a> [network](#module\_network) | github.com/patrickhayo/modules//vnet | n/a |
| <a name="module_nsg"></a> [nsg](#module\_nsg) | github.com/patrickhayo/modules//nsg | n/a |
| <a name="module_nsg_AzureBastionSubnet"></a> [nsg\_AzureBastionSubnet](#module\_nsg\_AzureBastionSubnet) | github.com/patrickhayo/modules//bastionhost | n/a |
| <a name="module_privatednszone"></a> [privatednszone](#module\_privatednszone) | github.com/patrickhayo/modules//privatednszone | n/a |

## Resources

| Name | Type |
|------|------|
| [azurerm_resource_group.this](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/resource_group) | resource |
| [azurerm_client_config.this](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/data-sources/client_config) | data source |
| [azurerm_resource_group.this](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/data-sources/resource_group) | data source |

## Inputs

No inputs.

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_basion"></a> [basion](#output\_basion) | n/a |
| <a name="output_nat"></a> [nat](#output\_nat) | n/a |
| <a name="output_network"></a> [network](#output\_network) | n/a |
| <a name="output_nsgs"></a> [nsgs](#output\_nsgs) | n/a |
| <a name="output_privatednszone"></a> [privatednszone](#output\_privatednszone) | n/a |
<!-- END_TF_DOCS -->
## Authors

Originally created by [Patrick Hayo](http://github.com/patrickhayo)

## License

[MIT](LICENSE) License - Copyright (c) 2022 by the Author.
