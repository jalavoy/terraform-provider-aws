---
subcategory: "CloudWatch Logs"
layout: "aws"
page_title: "AWS: aws_cloudwatch_log_group"
description: |-
  Get information on a Cloudwatch Log Group.
---

# Data Source: aws_cloudwatch_log_group

Use this data source to get information about an AWS Cloudwatch Log Group

## Example Usage

```terraform
data "aws_cloudwatch_log_group" "example" {
  name = "MyImportantLogs"
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) Name of the Cloudwatch log group

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `arn` - ARN of the Cloudwatch log group. Any `:*` suffix added by the API, denoting all CloudWatch Log Streams under the CloudWatch Log Group, is removed for greater compatibility with other AWS services that do not accept the suffix.
* `creation_time` - Creation time of the log group, expressed as the number of milliseconds after Jan 1, 1970 00:00:00 UTC.
* `retention_in_days` - Number of days log events retained in the specified log group.
* `kms_key_id` - ARN of the KMS Key to use when encrypting log data.
* `tags` - Map of tags to assign to the resource.
