# azr-tf-example-simple-network

[Terraform](https://www.terraform.io) Example to build a **Simple Network Setup**

- Virutal Network (VNET)
- NAT Gateway
- Private DNS Zone
- Network Security Group
- Bastion Host

<!-- BEGIN_TF_DOCS -->
## Prerequisites

- [Terraform](https://releases.hashicorp.com/terraform/) v1.2.5+

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | >=3.0.0 |

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) | >=3.0.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_bastion_host"></a> [bastion\_host](#module\_bastion\_host) | github.com/patrickhayo/modules//bastionhost | n/a |
| <a name="module_nat"></a> [nat](#module\_nat) | github.com/patrickhayo/modules//nat | n/a |
| <a name="module_network"></a> [network](#module\_network) | github.com/patrickhayo/modules//vnet | n/a |
| <a name="module_nsg"></a> [nsg](#module\_nsg) | github.com/patrickhayo/modules//nsg | n/a |
| <a name="module_nsg_AzureBastionSubnet"></a> [nsg\_AzureBastionSubnet](#module\_nsg\_AzureBastionSubnet) | github.com/patrickhayo/modules//nsg | n/a |
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
| <a name="output_basion"></a> [basion](#output\_basion) | Basiton Host Module Settings (deployed). |
| <a name="output_nat"></a> [nat](#output\_nat) | NAT Gateway Module Settings (deployed). |
| <a name="output_network"></a> [network](#output\_network) | VNET Module Settings (deployed). |
| <a name="output_nsgs"></a> [nsgs](#output\_nsgs) | NSG Module Settings (deployed). |
| <a name="output_privatednszone"></a> [privatednszone](#output\_privatednszone) | Private DNZ Zone Module Settings (deployed). |

## Variables

```hcl
locals {
  resource_group_name                   = "rg-example-simple-network"
  location                              = "westeurope"
  vnet_name                             = "vn-example-simple"
  address_space                         = ["10.255.0.0/24"]
  nat_gateway_prefix_enabled            = false
  bastion_host_name                     = "bh-example-simple"
  private_dns_zone_name                 = "example.mydomain-simple.com"
  private_dns_zone_registration_enabled = true
  subnets = [
    {
      name : "AzureBastionSubnet"
      address_prefixes : ["10.255.0.0/26"]
      enforce_private_link_endpoint_network_policies : true
      enforce_private_link_service_network_policies : false
      service_endpoints : [
        "Microsoft.AzureActiveDirectory"
      ]
      deligation : {
        name : null
        service_delegation : {
          actions : null
          name : null
        }
      }
    },

    {
      name : "sn-example-endpoints"
      address_prefixes : ["10.255.0.64/26"]
      enforce_private_link_endpoint_network_policies : false
      enforce_private_link_service_network_policies : false
      service_endpoints : [
        "Microsoft.AzureActiveDirectory",
        "Microsoft.Storage",
      ]
      deligation : {
        name : null
        service_delegation : {
          actions : null
          name : null
        }
      }
    },
    {
      name : "sn-example-services"
      address_prefixes : ["10.255.0.128/25"]
      enforce_private_link_endpoint_network_policies : true
      enforce_private_link_service_network_policies : false
      service_endpoints : [
        "Microsoft.AzureActiveDirectory",
        "Microsoft.Storage",
      ]
      deligation : {
        name : null
        service_delegation : {
          actions : null
          name : null
        }
      }
    }
  ]
}
```


<!-- END_TF_DOCS -->
## Authors

Originally created by [Patrick Hayo](http://github.com/patrickhayo)

## License

[MIT](LICENSE) License - Copyright (c) 2022 by the Author.
