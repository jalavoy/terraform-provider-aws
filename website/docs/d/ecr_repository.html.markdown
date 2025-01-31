---
subcategory: "ECR (Elastic Container Registry)"
layout: "aws"
page_title: "AWS: aws_ecr_repository"
description: |-
    Provides details about an ECR Repository
---

# Data Source: aws_ecr_repository

The ECR Repository data source allows the ARN, Repository URI and Registry ID to be retrieved for an ECR repository.

## Example Usage

```terraform
data "aws_ecr_repository" "service" {
  name = "ecr-repository"
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) Name of the ECR Repository.
* `registry_id` - (Optional) Registry ID where the repository was created.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `arn` - Full ARN of the repository.
* `encryption_configuration` - Encryption configuration for the repository. See [Encryption Configuration](#encryption-configuration) below.
* `image_scanning_configuration` - Configuration block that defines image scanning configuration for the repository. See [Image Scanning Configuration](#image-scanning-configuration) below.
* `image_tag_mutability` - The tag mutability setting for the repository.
* `most_recent_image_tags` - List of image tags associated with the most recently pushed image in the repository.
* `repository_url` - URL of the repository (in the form `aws_account_id.dkr.ecr.region.amazonaws.com/repositoryName`).
* `tags` - Map of tags assigned to the resource.

### Encryption Configuration

* `encryption_type` - Encryption type to use for the repository, either `AES256` or `KMS`.
* `kms_key` - If `encryption_type` is `KMS`, the ARN of the KMS key used.

### Image Scanning Configuration

* `scan_on_push` - Whether images are scanned after being pushed to the repository.
