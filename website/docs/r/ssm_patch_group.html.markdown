---
subcategory: "SSM (Systems Manager)"
layout: "aws"
page_title: "AWS: aws_ssm_patch_group"
description: |-
  Provides an SSM Patch Group resource
---

# Resource: aws_ssm_patch_group

Provides an SSM Patch Group resource

## Example Usage

```terraform
resource "aws_ssm_patch_baseline" "production" {
  name             = "patch-baseline"
  approved_patches = ["KB123456"]
}

resource "aws_ssm_patch_group" "patchgroup" {
  baseline_id = aws_ssm_patch_baseline.production.id
  patch_group = "patch-group-name"
}
```

## Argument Reference

The following arguments are supported:

* `baseline_id` - (Required) The ID of the patch baseline to register the patch group with.
* `patch_group` - (Required) The name of the patch group that should be registered with the patch baseline.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The name of the patch group and ID of the patch baseline separated by a comma (`,`).
