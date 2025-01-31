---
subcategory: "Cloud Map"
layout: "aws"
page_title: "AWS: aws_service_discovery_public_dns_namespace"
description: |-
  Provides a Service Discovery Public DNS Namespace resource.
---

# Resource: aws_service_discovery_public_dns_namespace

Provides a Service Discovery Public DNS Namespace resource.

## Example Usage

```terraform
resource "aws_service_discovery_public_dns_namespace" "example" {
  name        = "hoge.example.com"
  description = "example"
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the namespace.
* `description` - (Optional) The description that you specify for the namespace when you create it.
* `tags` - (Optional) A map of tags to assign to the namespace. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The ID of a namespace.
* `arn` - The ARN that Amazon Route 53 assigns to the namespace when you create it.
* `hosted_zone` - The ID for the hosted zone that Amazon Route 53 creates when you create a namespace.
* `tags_all` - A map of tags assigned to the resource, including those inherited from the provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Import

Service Discovery Public DNS Namespace can be imported using the namespace ID, e.g.,

```
$ terraform import aws_service_discovery_public_dns_namespace.example 0123456789
```
