---
subcategory: "Amplify"
layout: "aws"
page_title: "AWS: aws_amplify_webhook"
description: |-
  Provides an Amplify Webhook resource.
---

# Resource: aws_amplify_webhook

Provides an Amplify Webhook resource.

## Example Usage

```terraform
resource "aws_amplify_app" "example" {
  name = "app"
}

resource "aws_amplify_branch" "master" {
  app_id      = aws_amplify_app.example.id
  branch_name = "master"
}

resource "aws_amplify_webhook" "master" {
  app_id      = aws_amplify_app.example.id
  branch_name = aws_amplify_branch.master.branch_name
  description = "triggermaster"
}
```

## Argument Reference

The following arguments are supported:

* `app_id` - (Required) Unique ID for an Amplify app.
* `branch_name` - (Required) Name for a branch that is part of the Amplify app.
* `description` - (Optional) Description for a webhook.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `arn` - ARN for the webhook.
* `url` - URL of the webhook.

## Import

Amplify webhook can be imported using a webhook ID, e.g.,

```
$ terraform import aws_amplify_webhook.master a26b22a0-748b-4b57-b9a0-ae7e601fe4b1
```
