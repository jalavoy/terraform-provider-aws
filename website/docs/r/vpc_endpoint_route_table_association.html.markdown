---
subcategory: "VPC (Virtual Private Cloud)"
layout: "aws"
page_title: "AWS: aws_vpc_endpoint_route_table_association"
description: |-
  Manages a VPC Endpoint Route Table Association
---

# Resource: aws_vpc_endpoint_route_table_association

Manages a VPC Endpoint Route Table Association

## Example Usage

```terraform
resource "aws_vpc_endpoint_route_table_association" "example" {
  route_table_id  = aws_route_table.example.id
  vpc_endpoint_id = aws_vpc_endpoint.example.id
}
```

## Argument Reference

The following arguments are supported:

* `route_table_id` - (Required) Identifier of the EC2 Route Table to be associated with the VPC Endpoint.
* `vpc_endpoint_id` - (Required) Identifier of the VPC Endpoint with which the EC2 Route Table will be associated.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - A hash of the EC2 Route Table and VPC Endpoint identifiers.

## Import

VPC Endpoint Route Table Associations can be imported using `vpc_endpoint_id` together with `route_table_id`,
e.g.,

```
$ terraform import aws_vpc_endpoint_route_table_association.example vpce-aaaaaaaa/rtb-bbbbbbbb
```
