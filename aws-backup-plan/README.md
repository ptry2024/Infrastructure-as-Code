## Authors

Created by [Phuc Truong](https://gitlab.com/phuctruonghoang) - hoangphuc1662@gmail.com

## License

This project is 100% Open Source and licensed under the [APACHE2](https://gitlab.com/phuctruonghoang/Infrastructure-as-Code/tree/master/aws-backup-plan/LICENSE) for full details.

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.4 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | ~> 4.8 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | ~> 4.8 |
| <a name="provider_aws.secondary"></a> [aws.secondary](#provider\_aws.secondary) | ~> 4.8 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_backup_plan.backup-plan](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/backup_plan) | resource |
| [aws_backup_selection.backup-selection-tag](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/backup_selection) | resource |
| [aws_backup_vault.backup-vault](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/backup_vault) | resource |
| [aws_backup_vault_lock_configuration.back-vault-lock](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/backup_vault_lock_configuration) | resource |
| [aws_iam_role.backup-iam-role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.backup-role-policy-attachment](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_iam_role_policy_attachment.s3-backup-role-policy-attachment](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_kms_alias.kms](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_alias) | resource |
| [aws_kms_key.kms-key](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_key) | resource |
| [aws_kms_replica_key.kms](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_replica_key) | resource |
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/caller_identity) | data source |
| [aws_iam_policy_document.backup-assume-role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_region.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/region) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_aws_kms_name"></a> [aws\_kms\_name](#input\_aws\_kms\_name) | The server-side encryption key that is used to protect your backups | `string` | `""` | no |
| <a name="input_backup_plan"></a> [backup\_plan](#input\_backup\_plan) | Configure back up plan | <pre>list(object({<br>    backup_plan_name      = optional(string)<br>    rule_name             = optional(string)<br>    backup_schedule       = optional(string)<br>    start_window          = optional(number)<br>    completion_window     = optional(number)<br>    continuous_backup     = optional(bool) # Available for RDS, S3, and SAP HANA on Amazon EC2 resources.<br>    backup_retention_days = optional(number)<br>    backup_resource_name  = optional(list(string))<br>    exclude_resource_name = optional(list(string))<br>    selection_tag_name    = optional(string)<br>    selection_tags = optional(list(object({<br>      type  = string<br>      key   = string<br>      value = string<br>    })))<br>  }))</pre> | <pre>[<br>  {}<br>]</pre> | no |
| <a name="input_backup_vault"></a> [backup\_vault](#input\_backup\_vault) | The name of back up vault | <pre>object({<br>    backup_vault_name = optional(string)<br>  })</pre> | `{}` | no |
| <a name="input_backup_vault_lock"></a> [backup\_vault\_lock](#input\_backup\_vault\_lock) | Configure vault lock to protect backup vault | <pre>object({<br>    enabled                       = bool<br>    vault_lock_max_retention_days = optional(number)<br>    vault_lock_min_retention_days = optional(number)<br>  })</pre> | <pre>{<br>  "enabled": false<br>}</pre> | no |

## Outputs

No outputs.
<!-- END_TF_DOCS -->