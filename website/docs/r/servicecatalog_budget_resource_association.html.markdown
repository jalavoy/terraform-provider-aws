---
subcategory: "Service Catalog"
layout: "aws"
page_title: "AWS: aws_servicecatalog_budget_resource_association"
description: |-
  Manages a Service Catalog Budget Resource Association
---

# Resource: aws_servicecatalog_budget_resource_association

Manages a Service Catalog Budget Resource Association.

-> **Tip:** A "resource" is either a Service Catalog portfolio or product.

## Example Usage

### Basic Usage

```terraform
resource "aws_servicecatalog_budget_resource_association" "example" {
  budget_name = "budget-pjtvyakdlyo3m"
  resource_id = "prod-dnigbtea24ste"
}
```

## Argument Reference

The following arguments are required:

* `budget_name` - (Required) Budget name.
* `resource_id` - (Required) Resource identifier.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - Identifier of the association.

## Timeouts

[Configuration options](https://developer.hashicorp.com/terraform/language/resources/syntax#operation-timeouts):

- `create` - (Default `3m`)
- `read` - (Default `10m`)
- `delete` - (Default `3m`)

## Import

`aws_servicecatalog_budget_resource_association` can be imported using the budget name and resource ID, e.g.,

```
$ terraform import aws_servicecatalog_budget_resource_association.example budget-pjtvyakdlyo3m:prod-dnigbtea24ste
```
