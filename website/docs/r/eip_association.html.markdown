---
subcategory: "EC2 (Elastic Compute Cloud)"
layout: "aws"
page_title: "AWS: aws_eip_association"
description: |-
  Provides an AWS EIP Association
---

# Resource: aws_eip_association

Provides an AWS EIP Association as a top level resource, to associate and
disassociate Elastic IPs from AWS Instances and Network Interfaces.

~> **NOTE:** Do not use this resource to associate an EIP to `aws_lb` or `aws_nat_gateway` resources. Instead use the `allocation_id` available in those resources to allow AWS to manage the association, otherwise you will see `AuthFailure` errors.

~> **NOTE:** `aws_eip_association` is useful in scenarios where EIPs are either
pre-existing or distributed to customers or users and therefore cannot be changed.

## Example Usage

```terraform
resource "aws_eip_association" "eip_assoc" {
  instance_id   = aws_instance.web.id
  allocation_id = aws_eip.example.id
}

resource "aws_instance" "web" {
  ami               = "ami-21f78e11"
  availability_zone = "us-west-2a"
  instance_type     = "t2.micro"

  tags = {
    Name = "HelloWorld"
  }
}

resource "aws_eip" "example" {
  domain = "vpc"
}
```

## Argument Reference

The following arguments are supported:

* `allocation_id` - (Optional) The allocation ID. This is required for EC2-VPC.
* `allow_reassociation` - (Optional, Boolean) Whether to allow an Elastic IP to
be re-associated. Defaults to `true` in VPC.
* `instance_id` - (Optional) The ID of the instance. This is required for
EC2-Classic. For EC2-VPC, you can specify either the instance ID or the
network interface ID, but not both. The operation fails if you specify an
instance ID unless exactly one network interface is attached.
* `network_interface_id` - (Optional) The ID of the network interface. If the
instance has more than one network interface, you must specify a network
interface ID.
* `private_ip_address` - (Optional) The primary or secondary private IP address
to associate with the Elastic IP address. If no private IP address is
specified, the Elastic IP address is associated with the primary private IP
address.
* `public_ip` - (Optional) The Elastic IP address. This is required for EC2-Classic.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `association_id` - The ID that represents the association of the Elastic IP
address with an instance.
* `allocation_id` - As above
* `instance_id` - As above
* `network_interface_id` - As above
* `private_ip_address` - As above
* `public_ip` - As above

## Import

EIP Assocations can be imported using their association ID.

```
$ terraform import aws_eip_association.test eipassoc-ab12c345
```
