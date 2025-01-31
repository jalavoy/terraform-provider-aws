---
subcategory: "CloudWatch RUM"
layout: "aws"
page_title: "AWS: aws_rum_metrics_destination"
description: |-
  Provides a CloudWatch RUM Metrics Destination resource.
---

# Resource: aws_rum_metrics_destination

Provides a CloudWatch RUM Metrics Destination resource.

## Example Usage

```terraform
resource "aws_rum_metrics_destination" "example" {
  app_monitor_name = aws_rum_app_monitor.example.name
  destination      = "CloudWatch"
}
```

## Argument Reference

The following arguments are supported:

* `app_monitor_name` - (Required) The name of the CloudWatch RUM app monitor that will send the metrics.
* `destination` - (Required)  Defines the destination to send the metrics to. Valid values are `CloudWatch` and `Evidently`. If you specify `Evidently`, you must also specify the ARN of the CloudWatchEvidently experiment that is to be the destination and an IAM role that has permission to write to the experiment.
* `destination_arn` - (Optional) Use this parameter only if Destination is Evidently. This parameter specifies the ARN of the Evidently experiment that will receive the extended metrics.
* `iam_role_arn` - (Optional) This parameter is required if Destination is Evidently. If Destination is CloudWatch, do not use this parameter.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The name of the CloudWatch RUM app monitor that will send the metrics.

## Import

Cloudwatch RUM Metrics Destination can be imported using the `id`, e.g.,

```
$ terraform import aws_rum_metrics_destination.example example
```
