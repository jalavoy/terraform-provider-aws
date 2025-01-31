---
subcategory: "Service Catalog"
layout: "aws"
page_title: "AWS: aws_servicecatalog_tag_option"
description: |-
  Manages a Service Catalog Tag Option
---

# Resource: aws_servicecatalog_tag_option

Manages a Service Catalog Tag Option.

## Example Usage

### Basic Usage

```terraform
resource "aws_servicecatalog_tag_option" "example" {
  key   = "nyckel"
  value = "värde"
}
```

## Argument Reference

The following arguments are required:

* `key` - (Required) Tag option key.
* `value` - (Required) Tag option value.

The following arguments are optional:

* `active` - (Optional) Whether tag option is active. Default is `true`.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - Identifier (e.g., `tag-pjtvagohlyo3m`).
* `owner_id` - AWS account ID of the owner account that created the tag option.

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `create` - (Default `3m`)
- `read` - (Default `10m`)
- `update` - (Default `3m`)
- `delete` - (Default `3m`)

## Import

`aws_servicecatalog_tag_option` can be imported using the tag option ID, e.g.,

```
$ terraform import aws_servicecatalog_tag_option.example tag-pjtvagohlyo3m
```
