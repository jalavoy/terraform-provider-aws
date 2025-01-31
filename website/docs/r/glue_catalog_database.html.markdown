---
subcategory: "Glue"
layout: "aws"
page_title: "AWS: aws_glue_catalog_database"
description: |-
  Provides a Glue Catalog Database.
---

# Resource: aws_glue_catalog_database

Provides a Glue Catalog Database Resource. You can refer to the [Glue Developer Guide](http://docs.aws.amazon.com/glue/latest/dg/populate-data-catalog.html) for a full explanation of the Glue Data Catalog functionality

## Example Usage

```terraform
resource "aws_glue_catalog_database" "aws_glue_catalog_database" {
  name = "MyCatalogDatabase"
}
```

### Create Table Default Permissions

```terraform
resource "aws_glue_catalog_database" "aws_glue_catalog_database" {
  name = "MyCatalogDatabase"

  create_table_default_permission {
    permissions = ["SELECT"]

    principal {
      data_lake_principal_identifier = "IAM_ALLOWED_PRINCIPALS"
    }
  }
}
```

## Argument Reference

The following arguments are supported:

* `catalog_id` - (Optional) ID of the Glue Catalog to create the database in. If omitted, this defaults to the AWS Account ID.
* `create_table_default_permission` - (Optional) Creates a set of default permissions on the table for principals. See [`create_table_default_permission`](#create_table_default_permission) below.
* `description` - (Optional) Description of the database.
* `location_uri` - (Optional) Location of the database (for example, an HDFS path).
* `name` - (Required) Name of the database. The acceptable characters are lowercase letters, numbers, and the underscore character.
* `parameters` - (Optional) List of key-value pairs that define parameters and properties of the database.
* `tags` - (Optional) Key-value map of resource tags. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.
* `target_database` - (Optional) Configuration block for a target database for resource linking. See [`target_database`](#target_database) below.

### target_database

* `catalog_id` - (Required) ID of the Data Catalog in which the database resides.
* `database_name` - (Required) Name of the catalog database.
* `region` - (Optional) Region of the target database.

### create_table_default_permission

* `permissions` - (Optional) The permissions that are granted to the principal.
* `principal` - (Optional) The principal who is granted permissions.. See [`principal`](#principal) below.

#### principal

* `data_lake_principal_identifier` - (Optional) An identifier for the Lake Formation principal.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `arn` - ARN of the Glue Catalog Database.
* `id` - Catalog ID and name of the database.
* `tags_all` - A map of tags assigned to the resource, including those inherited from the provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Import

Glue Catalog Databases can be imported using the `catalog_id:name`. If you have not set a Catalog ID specify the AWS Account ID that the database is in, e.g.,

```
$ terraform import aws_glue_catalog_database.database 123456789012:my_database
```
