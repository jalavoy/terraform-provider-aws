---
subcategory: "API Gateway"
layout: "aws"
page_title: "AWS: aws_api_gateway_documentation_version"
description: |-
  Provides a resource to manage an API Gateway Documentation Version.
---

# Resource: aws_api_gateway_documentation_version

Provides a resource to manage an API Gateway Documentation Version.

## Example Usage

```terraform
resource "aws_api_gateway_documentation_version" "example" {
  version     = "example_version"
  rest_api_id = aws_api_gateway_rest_api.example.id
  description = "Example description"
  depends_on  = [aws_api_gateway_documentation_part.example]
}

resource "aws_api_gateway_rest_api" "example" {
  name = "example_api"
}

resource "aws_api_gateway_documentation_part" "example" {
  location {
    type = "API"
  }

  properties  = "{\"description\":\"Example\"}"
  rest_api_id = aws_api_gateway_rest_api.example.id
}
```

## Argument Reference

The following argument is supported:

* `version` - (Required) Version identifier of the API documentation snapshot.
* `rest_api_id` - (Required) ID of the associated Rest API
* `description` - (Optional) Description of the API documentation version.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

## Import

API Gateway documentation versions can be imported using `REST-API-ID/VERSION`, e.g.,

```
$ terraform import aws_api_gateway_documentation_version.example 5i4e1ko720/example-version
```
