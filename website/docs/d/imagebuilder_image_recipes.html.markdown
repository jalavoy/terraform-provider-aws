---
subcategory: "EC2 Image Builder"
layout: "aws"
page_title: "AWS: aws_imagebuilder_image_recipes"
description: |-
    Get information on Image Builder Image Recipes.
---

# Data Source: aws_imagebuilder_image_recipes

Use this data source to get the ARNs and names of Image Builder Image Recipes matching the specified criteria.

## Example Usage

```terraform
data "aws_imagebuilder_image_recipes" "example" {
  owner = "Self"

  filter {
    name   = "platform"
    values = ["Linux"]
  }
}
```

## Argument Reference

* `owner` - (Optional) Owner of the image recipes. Valid values are `Self`, `Shared` and `Amazon`. Defaults to `Self`.
* `filter` - (Optional) Configuration block(s) for filtering. Detailed below.

### filter Configuration Block

The following arguments are supported by the `filter` configuration block:

* `name` - (Required) Name of the filter field. Valid values can be found in the [Image Builder ListImageRecipes API Reference](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_ListImageRecipes.html).
* `values` - (Required) Set of values that are accepted for the given filter field. Results will be selected if any given value matches.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `arns` - Set of ARNs of the matched Image Builder Image Recipes.
* `names` - Set of names of the matched Image Builder Image Recipes.
