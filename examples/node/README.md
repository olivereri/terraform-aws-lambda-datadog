# Node Example

A simple Node Lambda function with out of the box Datadog instrumentation.

## Usage

* Create a [Datadog API Key](https://app.datadoghq.com/organization-settings/api-keys)
* Create a secret in [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html) and add the Datadog API Key as the secret value in plaintext
* Create a `terraform.tfvars` file
  - Set the `datadog_secret_arn` to the arn of the secret you just created
  - Set the `datadog_service_name` to the name of the service you want to use to filter for the resource in Datadog
* Run the following commands

```
terraform init
terraform plan
terraform apply
```

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.3 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 5.32.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_archive"></a> [archive](#provider\_archive) | 2.4.2 |
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 5.32.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_example_lambda_function"></a> [example\_lambda\_function](#module\_example\_lambda\_function) | ../../ | n/a |

## Resources

| Name | Type |
|------|------|
| [aws_iam_policy.secrets_manager_read_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_role.lambda_role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.attach_iam_policy_to_iam_role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_iam_role_policy_attachment.attach_secrets_manager_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [archive_file.zip_code](https://registry.terraform.io/providers/hashicorp/archive/latest/docs/data-sources/file) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_secret_arn"></a> [secret\_arn](#input\_secret\_arn) | Secret for Datadog API Key | `string` | n/a | yes |
| <a name="input_service_name"></a> [service\_name](#input\_service\_name) | Service used to filter for resources in Datadog | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_arn"></a> [arn](#output\_arn) | Amazon Resource Name (ARN) identifying your Lambda Function. |
| <a name="output_function_name"></a> [function\_name](#output\_function\_name) | Unique name for your Lambda Function |
| <a name="output_invoke_arn"></a> [invoke\_arn](#output\_invoke\_arn) | ARN to be used for invoking Lambda Function from API Gateway. |
<!-- END_TF_DOCS -->
