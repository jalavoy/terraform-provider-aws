---
subcategory: "WAF Classic Regional"
layout: "aws"
page_title: "AWS: aws_wafregional_xss_match_set"
description: |-
  Provides an AWS WAF Regional XSS Match Set resource for use with ALB.
---

# Resource: aws_wafregional_xss_match_set

Provides a WAF Regional XSS Match Set Resource for use with Application Load Balancer.

## Example Usage

```terraform
resource "aws_wafregional_xss_match_set" "xss_match_set" {
  name = "xss_match_set"

  xss_match_tuple {
    text_transformation = "NONE"

    field_to_match {
      type = "URI"
    }
  }

  xss_match_tuple {
    text_transformation = "NONE"

    field_to_match {
      type = "QUERY_STRING"
    }
  }
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the set
* `xss_match_tuple` - (Optional) The parts of web requests that you want to inspect for cross-site scripting attacks.

### Nested fields

#### `xss_match_tuple`

* `field_to_match` - (Required) Specifies where in a web request to look for cross-site scripting attacks.
* `text_transformation` - (Required) Which text transformation, if any, to perform on the web request before inspecting the request for cross-site scripting attacks.

#### `field_to_match`

* `data` - (Optional) When the value of `type` is `HEADER`, enter the name of the header that you want the WAF to search, for example, `User-Agent` or `Referer`. If the value of `type` is any other value, omit `data`.
* `type` - (Required) The part of the web request that you want AWS WAF to search for a specified stringE.g., `HEADER` or `METHOD`

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The ID of the Regional WAF XSS Match Set.

## Import

AWS WAF Regional XSS Match can be imported using the `id`, e.g.,

```sh
$ terraform import aws_wafregional_xss_match_set.example 12345abcde
```
