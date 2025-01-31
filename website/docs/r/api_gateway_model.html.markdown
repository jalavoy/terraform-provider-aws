---
subcategory: "API Gateway"
layout: "aws"
page_title: "AWS: aws_api_gateway_model"
description: |-
  Provides a Model for a REST API Gateway.
---

# Resource: aws_api_gateway_model

Provides a Model for a REST API Gateway.

## Example Usage

```terraform
resource "aws_api_gateway_rest_api" "MyDemoAPI" {
  name        = "MyDemoAPI"
  description = "This is my API for demonstration purposes"
}

resource "aws_api_gateway_model" "MyDemoModel" {
  rest_api_id  = aws_api_gateway_rest_api.MyDemoAPI.id
  name         = "user"
  description  = "a JSON schema"
  content_type = "application/json"

  schema = jsonencode({
    type = "object"
  })
}
```

## Argument Reference

The following arguments are supported:

* `rest_api_id` - (Required) ID of the associated REST API
* `name` - (Required) Name of the model
* `description` - (Optional) Description of the model
* `content_type` - (Required) Content type of the model
* `schema` - (Required) Schema of the model in a JSON form

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - ID of the model

## Import

`aws_api_gateway_model` can be imported using `REST-API-ID/NAME`, e.g.,

```
$ terraform import aws_api_gateway_model.example 12345abcde/example
```
