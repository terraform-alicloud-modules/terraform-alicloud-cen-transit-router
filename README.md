Terraform module which creates CEN Transit Router resources on Alibaba Cloud.

terraform-alicloud-cen-transit-router
=====================================================================

English | [简体中文](https://github.com/terraform-alicloud-modules/terraform-alicloud-cen-transit-router/blob/main/README-CN.md)

This module is used to create CEN Transit Router resources on Alibaba Cloud.

These types of resources are supported:

* [alicloud_cen_transit_router](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/cen_transit_router)
* [alicloud_cen_transit_router_route_table](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/cen_transit_router_route_table)
* [alicloud_cen_transit_router_vpc_attachment](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/cen_transit_router_vpc_attachment)
* [alicloud_cen_transit_router_route_entry](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/cen_transit_router_route_entry)
* [alicloud_cen_route_map](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/cen_route_map)

## Usage

```hcl
module "example" {
  source                                 = "terraform-alicloud-modules/cen-transit-router/alicloud"
  #alicloud_cen_transit_router
  create_transit_router                  = true
  transit_router_name                    = "tf-test-transit-router"
  transit_router_description             = "tf-test-transit-router"
  cen_id                                 = "your_cen_id"
  #alicloud_cen_transit_router_route_table
  create_route_table                     = true
  transit_router_route_table_name        = "tf-test-route-table"
  transit_router_route_table_description = "tf-test-route-table"
  #alicloud_cen_transit_router_vpc_attachment
  create_vpc_attachment                 = true
  vpc_id                                = "your_vpc_id"
  transit_router_attachment_name        = "tf-test-vpc-attachment"
  transit_router_attachment_description = "tf-test-vpc-attachment"
  zone_mappings                         = [{ zone_id : "cn-hangzhou-h", vswitch_id : your_master_vswitch_id }, { zone_id : "cn-hangzhou-i", vswitch_id : your_slave_vswitch_id }]
  #alicloud_cen_transit_router_route_entry
  create_route_entry                                = true
  transit_router_route_entry_destination_cidr_block = "192.168.0.0/24"
  transit_router_route_entry_next_hop_type          = "Attachment"
  transit_router_route_entry_name                   = "tf-test-route-entry"
  transit_router_route_entry_description            = "tf-test-route-entry"
  #alicloud_cen_route_map
  create_route_map                       = true
  cen_region_id                          = "cn-hangzhou"
  route_map_description                  = "tf-test-route-map"
  priority                               = 1
  transmit_direction                     = "RegionIn"
  map_result                             = "Permit"
  source_region_ids                      = ["cn-beijing"]
}
```

## Examples

* [complete example](https://github.com/terraform-alicloud-modules/terraform-alicloud-cen-transit-router/tree/main/examples/complete)

## Notes

* This module using AccessKey and SecretKey are from `profile` and `shared_credentials_file`. If you have not set them
  yet, please install [aliyun-cli](https://github.com/aliyun/aliyun-cli#installation) and configure it.

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | > = 0.13 |
| <a name="requirement_alicloud"></a> [alicloud](#requirement\_alicloud) | > = 1.126.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_alicloud"></a> [alicloud](#provider\_alicloud) | > = 1.126.0 |

## Submit Issues

If you have any problems when using this module, please opening
a [provider issue](https://github.com/aliyun/terraform-provider-alicloud/issues/new) and let us know.

**Note:** There does not recommend opening an issue on this repo.

## Authors

Created and maintained by Alibaba Cloud Terraform Team(terraform@alibabacloud.com).

## License

MIT Licensed. See LICENSE for full details.

## Reference

* [Terraform-Provider-Alicloud Github](https://github.com/aliyun/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs)
