+++
title = "scim_group"
date = 2020-04-20T23:34:03-04:00
weight = 15
chapter = false
pre = ""
+++

## Resource: `databricks_scim_group`

This resource allows you to create groups in Databricks. You can also associate Databricks users to the following groups. 

{{% notice note %}} 
You must be a Databricks administrator API token to use SCIM resources.
{{% /notice %}} 

## Example Usage

```hcl
resource "databricks_scim_user" "my-user" {
  user_name = "testuser@databricks.com"
  display_name = "Test User"
  entitlements = [
    "allow-cluster-create",
  ]
}

resource "databricks_scim_group" "my-group" {
  display_name = "Sri Test Group"
  members = ["${databricks_scim_user.my-user.id}"]
}
```
## Argument Reference

The following arguments are supported:

#### - `display_name`:
> **(Required)** This is the display name for the given group.

#### - `group_members`:
> **(Optional)** This is a list of users associated to the given group.

#### - `roles`:
> **(Optional)** This is the list of roles that you wish to attach to this group.

#### - `entitlements`:
> **(Optional)** This is the list of entitlements that you wish to attach to this group.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

#### - `id`:
> The id for the scim group object.

#### - `inherited_roles`:
> The list of roles inherited by parent groups that this group is a member of.

## Import

{{% notice note %}}
Importing this resource is not currently supported.
{{% /notice %}}
