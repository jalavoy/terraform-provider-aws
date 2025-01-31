---
subcategory: "IAM (Identity & Access Management)"
layout: "aws"
page_title: "AWS: aws_iam_user_policy"
description: |-
  Provides an IAM policy attached to a user.
---

# Resource: aws_iam_user_policy

Provides an IAM policy attached to a user.

## Example Usage

```terraform
resource "aws_iam_user_policy" "lb_ro" {
  name = "test"
  user = aws_iam_user.lb.name

  # Terraform's "jsonencode" function converts a
  # Terraform expression result to valid JSON syntax.
  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Action = [
          "ec2:Describe*",
        ]
        Effect   = "Allow"
        Resource = "*"
      },
    ]
  })
}

resource "aws_iam_user" "lb" {
  name = "loadbalancer"
  path = "/system/"
}

resource "aws_iam_access_key" "lb" {
  user = aws_iam_user.lb.name
}
```

## Argument Reference

The following arguments are supported:

* `policy` - (Required) The policy document. This is a JSON formatted string. For more information about building AWS IAM policy documents with Terraform, see the [AWS IAM Policy Document Guide](https://learn.hashicorp.com/terraform/aws/iam-policy).
* `name` - (Optional) The name of the policy. If omitted, Terraform will assign a random, unique name.
* `name_prefix` - (Optional, Forces new resource) Creates a unique name beginning with the specified prefix. Conflicts with `name`.
* `user` - (Required) IAM user to which to attach this policy.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The user policy ID, in the form of `user_name:user_policy_name`.
* `name` - The name of the policy (always set).

## Import

IAM User Policies can be imported using the `user_name:user_policy_name`, e.g.,

```
$ terraform import aws_iam_user_policy.mypolicy user_of_mypolicy_name:mypolicy_name
```
